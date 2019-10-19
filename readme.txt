For PCIe RIFFA link:
==========================================================================
https://sites.google.com/a/eng.ucsd.edu/matt-jacobsen/riffa/riffa_2_0/download/download_agreed


The IBUFDS location:
==========================================================================
100 MHz Reference Clock: 
 #NET "sys_clk_p" LOC = P6; 
 #NET "sys_clk_n" LOC = P5; 
INST "refclk_ibuf" LOC = IBUFDS_GTXE1_X0Y6; 
 
250 MHz Reference Clock: 
 #NET "sys_clk_p" LOC = V6; 
 #NET "sys_clk_n" LOC = V5; 
INST "refclk_ibuf" LOC = IBUFDS_GTXE1_X0Y4; 





RIFFA driver sign:
==========================================================================
SignTool sign /v /a /t  http://timestamp.digicert.com  *******.sys
SignTool sign /v /a /t  http://timestamp.digicert.com  *******.cat




add the line at gtx_wrapper_v6.v at ip core of PCIe
modify "xxxxxxxxxxxxxxx"
==========================================================================
`include "../xxxxxxxxxxxxxxx/xxxxxxxxxxxxxxx/source/gtx_drp_chanalign_fix_3752_v6.v"



add the line after // at gtx_wrapper_v6.v after ip generated
==========================================================================
//.TX_DETECT_RX_CFG( 14'h1832 ),
.TX_DETECT_RX_CFG( 14'h1032 ),
