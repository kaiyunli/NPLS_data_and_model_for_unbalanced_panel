# NPLS_data_and_model_for_unbalanced_panel
安装说明：
1. 所需文件：xthreg.zip，xthreginstall.ado 
2. 安装步骤： 
[1] 将压缩文件 xthreg.zip（无需解压），以及文件 xthreginstall.ado
保存到某个目录，比如”c:\stataplus”。 
[2] 运行 Stata，设置当前工作目录为"c:\stataplus": 
. cd "c:\stataplus" 
[3]  输入指令： 
. xthreginstall

代码实例：
clear
cls
cd "/Users/ky/Desktop/毕业设计/代码集"
import delimited "/Users/ky/Desktop/毕业设计/代码集/dat.csv"
xtset id year
tabstat npl lgr dgr er car homo lnsize gdp,stat(n me ma mi med sd)

xi:xthreg npl homo dgr er lnsize gdp i.year,rx(lgr) qx(lag_npl) thnum(1) bs(300) trim(0.02) grid(300) 
est store model4
estat plot 
estat summ 
