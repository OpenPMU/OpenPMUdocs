# Decoding OpenPMU V2 Sampled Values from Base64

This method can be implemented in many development environments.  A visual example is given here to help understanding.

## Original Base64

The following is 128 sampled values, 16-bit signed integers, encoded in Base64.

`JWMmESa8J2QoBCieKTEpuypAKrwrMSufLAYsZSy+LQ8tWS2bLdcuCS40LlUucC6CLn4uai5PLiot/y3KLY4tSSz+LKssUivyK4srGyqoKispqSkfKI8n9ydZJrUmCiVXJJ8j4CMaIk8heyClH8ce4x36HQwcGRsgGiIZIRgbFxEWBBTyE90SxhGqEIwPaw5IDSQL/ArUCaoIfQdRBiME9QPGApYBaAA5/wr92/yt+4H6Vfks+AL23PW49JXzdfJX8T7wJ+8S7gPs9+vt6ujp6Ojs5/XnA+YX5S/kTeNv4pnhyOD94Djfet7D3hLdZ9zC3CXbjtr+2nXZ89l42QTYlg==
`

The workflow to decode this back to decimal represention is visualised well using https://cryptii.com/

![Cryptii Example](/Base64_Decode/DecodeBase64UsingCryptii.PNG)

In Hex:

`2563 2611 26bc 2764 2804 289e 2931 29bb 2a40 2abc 2b31 2b9f 2c06 2c65 2cbe 2d0f 2d59 2d9b 2dd7 2e09 2e34 2e55 2e70 2e82 2e7e 2e6a 2e4f 2e2a 2dff 2dca 2d8e 2d49 2cfe 2cab 2c52 2bf2 2b8b 2b1b 2aa8 2a2b 29a9 291f 288f 27f7 2759 26b5 260a 2557 249f 23e0 231a 224f 217b 20a5 1fc7 1ee3 1dfa 1d0c 1c19 1b20 1a22 1921 181b 1711 1604 14f2 13dd 12c6 11aa 108c 0f6b 0e48 0d24 0bfc 0ad4 09aa 087d 0751 0623 04f5 03c6 0296 0168 0039 ff0a fddb fcad fb81 fa55 f92c f802 f6dc f5b8 f495 f375 f257 f13e f027 ef12 ee03 ecf7 ebed eae8 e9e8 e8ec e7f5 e703 e617 e52f e44d e36f e299 e1c8 e0fd e038 df7a dec3 de12 dd67 dcc2 dc25 db8e dafe da75 d9f3 d978 d904 d896
`

In Decimal:

`9571 9745 9916 10084 10244 10398 10545 10683 10816 10940 11057 11167 11270 11365 11454 11535 11609 11675 11735 11785 11828 11861 11888 11906 11902 11882 11855 11818 11775 11722 11662 11593 11518 11435 11346 11250 11147 11035 10920 10795 10665 10527 10383 10231 10073 9909 9738 9559 9375 9184 8986 8783 8571 8357 8135 7907 7674 7436 7193 6944 6690 6433 6171 5905 5636 5362 5085 4806 4522 4236 3947 3656 3364 3068 2772 2474 2173 1873 1571 1269 966 662 360 57 -246 -549 -851 -1151 -1451 -1748 -2046 -2340 -2632 -2923 -3211 -3497 -3778 -4057 -4334 -4605 -4873 -5139 -5400 -5656 -5908 -6155 -6397 -6633 -6865 -7091 -7313 -7527 -7736 -7939 -8136 -8326 -8509 -8686 -8857 -9022 -9179 -9330 -9474 -9611 -9741 -9864 -9980 -10090
`

Graphically:

![Excel Chart](/Base64_Decode/Base64ExampleChart.PNG)
