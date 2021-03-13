# OpenPMU V2 - XML Datagrams

The purpose of this document is to describe the XML datagram formats used within OpenPMU V2.  There are two main datagrams in use in OpenPMU:

* XML Sampled Values
* XML Phasor Values

## Overview

In OpenPMU V2, all aspects of the Phasor Measurement Unit data pipeline are rigidly modular.  The three important modules in the pipeline are:

* Data Acquisition (Usually an ADC, sometimes simulator or playback of recordings).
** Produces a stream of sampled values formatted in XML.
* Phasor Estimation (estimates phasors from sampled values).
** Produces a stream of phasors formatted in XML.
* Telecommunications (Usually an IEEE C37.118.2 or IEC 61850-90-5 adapter).
** Provides, for example, a TCP socket with which to connect by IEEE C37.118.2.

You can find a detailed description of OpenPMU's modular configuration and data flows in [this paper](https://ieeexplore.ieee.org/document/8273986):

`D. M. Laverty, J. Hastings, D. J. Morrow, R. Khan, K. Mclaughlin and S. Sezer, "A modular phasor measurement unit design featuring open data exchange methods," 2017 IEEE Power & Energy Society General Meeting, Chicago, IL, USA, 2017, pp. 1-5, doi: 10.1109/PESGM.2017.8273986.`

Although XML is traditionally used to markup data in files, in OpenPMU it is used to markup data in streams of UDP datagrams.  This makes the modules in OpenPMU completely plug and play, yielding a higly flexible system.

The next sections provide a brief description of the XML datagram structures intended to help developers working on the OpenPMU system.

## XML Sampled Values Datagram

An example of the datagram is given below.  The first section of the datagram contains important metadata describing the structure of the sampled values.  

* **Date** and **Time** refer to the time at which the first sampled value (SV) in each payload was taken.  Note: All channels are synchronously sampled, so sample 0 of Channel_0 was acquired at the same time as sample 0 of Channel_1, etc.  

* **Frame** is a sequence number which is useful to determine if frames of data have been dropped.  Normally, the frames are sent at a rate of 2x the nominal system frequency, so on a 50 Hz system the frame number increments from 0 to 99 and then loops to 0.  On a 60 Hz system, it loops between 0 and 119.

* **Fs** is the sampling rate / sample frequency of the ADC.  The period between sampled values (__Ts__) is given as __Ts = 1 / Fs__.  In this example, the sampling rate is 12,800 Hz, so the period is 78.125 μs.  This means that sample 1 occurs at time 22:04:00.000078125, and sample 2 occurs at 22:04:00.00015625, and so on.

* **n** is the number of sampled values in each __Payload__.  Here there are 128 sampled values in each payload.  Multiplying __n__ by __Ts__ tells us that the payload represents 10 ms of waveform data.

* **bits** is the number of bits per sampled value.  In this case, 16 means that the sampled values are expressed as 16-bit signed integers.

* **Channels** is the number of channels of data contained in this datagram.  In this case, there are 3 channels.

Each channel is described as starting with a tag named **Channel_N** where __N__ starts at 0.  Within this tag there is metadata which is unique to that channel, and then the payload of sampled values.

* **Name** is the name of that channel.  Here the channel name is '__Belfast_Va__'.  This name is used to name the phasors produced by the phasor estimator, and ultimately by the Telecoms interface.

* **Type** states if the channel is a voltage channel '__V__' or a current channel '__I__'.

* **Phase** states which phase the channel represents.  This is useful when storing data from polyphase circuits as it avoids having to parse such information from the __Name__ tag, which might in the case of some end users may employ an esoteric naming convention.  Typically these are labelled '__a__', '__b__', '__c__', '__n__'.

* **Range** states the full scale deflection of the sampled values.  In the case of signed 16-bit integers, this means that a value of 32,768 equates to a voltage of 275 V.

* **Payload** the payload is the sampled values encoded in Base64.  The reason for this is to map the binary data to a set of ASCII characters so that the datagrams can be passed and parsed through virtually any data manipulation tool.  There is a trade off as it increases the size of the datagrams, but since these datagrams are intended for inter-module communication, often on the same localhost or devices in the same physical enclosure, this does not lead to any issues re bandwidth on external networks.

```xml
<OpenPMU>
	<Date>2021-02-28</Date>
	<Time>22:04:00.000</Time>
	<Frame>0</Frame>
	<Fs>12800</Fs>
	<n>128</n>
	<bits>16</bits>
	<Channels>3</Channels>
	<Channel_0>
		<Name>Belfast_Va</Name>
		<Type>V</Type>
		<Phase>a</Phase>
		<Range>275</Range>
		<Payload>JWMmESa8J2QoBCieKTEpuypAKrwrMSufLAYsZSy+LQ8tWS2bLdcuCS40LlUucC6CLn4uai5PLiot/y3KLY4tSSz+LKssUivyK4srGyqoKispqSkfKI8n9ydZJrUmCiVXJJ8j4CMaIk8heyClH8ce4x36HQwcGRsgGiIZIRgbFxEWBBTyE90SxhGqEIwPaw5IDSQL/ArUCaoIfQdRBiME9QPGApYBaAA5/wr92/yt+4H6Vfks+AL23PW49JXzdfJX8T7wJ+8S7gPs9+vt6ujp6Ojs5/XnA+YX5S/kTeNv4pnhyOD94Djfet7D3hLdZ9zC3CXbjtr+2nXZ89l42QTYlg==</Payload>
	</Channel_0>
	<Channel_1>
		<Name>Belfast_Vb</Name>
		<Type>V</Type>
		<Phase>b</Phase>
		<Range>275</Range>
		<Payload>  ..Base64..  </Payload>
	</Channel_1>
	<Channel_2>
		<Name>Belfast_Vc</Name>
		<Type>V</Type>
		<Phase>c</Phase>
		<Range>275</Range>
		<Payload>  ..Base64..  </Payload>
	</Channel_2>
</OpenPMU>
```
