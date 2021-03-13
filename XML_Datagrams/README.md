The purpose of this document is to describe the XML datagram formats used within OpenPMU V2.  There are two main datagrams in use in OpenPMU:

* XML Sampled Values
* XML Phasor Values

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
