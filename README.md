# SQL_histogram
How to get an histogram from SQL query example with Python



```python
# get min and max from database

min = 25
max = 4.019691280088219E7
bins = 100

def get_thresholds(min, max, bins):
    x = []
    step=(max-min)/bins 
    for i in range(bins):
        x.append(round(i*step,2))
    return x

ths = get_thresholds(min,max,bins)

def histogram(ths, variable):
    q = []
    q.append("SELECT CASE ")
    for i in range(len(ths)-1):
        q_i =" WHEN "+variable+" >= " + str(ths[i]) +" AND " +variable+ " < "+ str(ths[i+1])+" THEN "+ str(ths[i+1]) 
        q.append(q_i)
    q.append(" WHEN  "+variable+" >= " + str(ths[i+1]) + " THEN "+ str(999999999))
    q.append(" ELSE NULL END as Score ")
    return q

variable = " l4_ul_goodput + l4_dw_goodput "
q = histogram(ths,variable)

for i in range(len(q)):
    print(q[i])

```



```SQL
--Example

Select Score, count(*) as Freq 
FROM ( 
SELECT CASE
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 0.0 AND  l4_ul_goodput + l4_dw_goodput  < 401968.88 THEN 401968.88
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 401968.88 AND  l4_ul_goodput + l4_dw_goodput  < 803937.76 THEN 803937.76
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 803937.76 AND  l4_ul_goodput + l4_dw_goodput  < 1205906.63 THEN 1205906.63
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 1205906.63 AND  l4_ul_goodput + l4_dw_goodput  < 1607875.51 THEN 1607875.51
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 1607875.51 AND  l4_ul_goodput + l4_dw_goodput  < 2009844.39 THEN 2009844.39
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 2009844.39 AND  l4_ul_goodput + l4_dw_goodput  < 2411813.27 THEN 2411813.27
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 2411813.27 AND  l4_ul_goodput + l4_dw_goodput  < 2813782.15 THEN 2813782.15
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 2813782.15 AND  l4_ul_goodput + l4_dw_goodput  < 3215751.02 THEN 3215751.02
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 3215751.02 AND  l4_ul_goodput + l4_dw_goodput  < 3617719.9 THEN 3617719.9
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 3617719.9 AND  l4_ul_goodput + l4_dw_goodput  < 4019688.78 THEN 4019688.78
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 4019688.78 AND  l4_ul_goodput + l4_dw_goodput  < 4421657.66 THEN 4421657.66
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 4421657.66 AND  l4_ul_goodput + l4_dw_goodput  < 4823626.54 THEN 4823626.54
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 4823626.54 AND  l4_ul_goodput + l4_dw_goodput  < 5225595.41 THEN 5225595.41
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 5225595.41 AND  l4_ul_goodput + l4_dw_goodput  < 5627564.29 THEN 5627564.29
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 5627564.29 AND  l4_ul_goodput + l4_dw_goodput  < 6029533.17 THEN 6029533.17
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 6029533.17 AND  l4_ul_goodput + l4_dw_goodput  < 6431502.05 THEN 6431502.05
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 6431502.05 AND  l4_ul_goodput + l4_dw_goodput  < 6833470.93 THEN 6833470.93
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 6833470.93 AND  l4_ul_goodput + l4_dw_goodput  < 7235439.8 THEN 7235439.8
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 7235439.8 AND  l4_ul_goodput + l4_dw_goodput  < 7637408.68 THEN 7637408.68
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 7637408.68 AND  l4_ul_goodput + l4_dw_goodput  < 8039377.56 THEN 8039377.56
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 8039377.56 AND  l4_ul_goodput + l4_dw_goodput  < 8441346.44 THEN 8441346.44
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 8441346.44 AND  l4_ul_goodput + l4_dw_goodput  < 8843315.32 THEN 8843315.32
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 8843315.32 AND  l4_ul_goodput + l4_dw_goodput  < 9245284.19 THEN 9245284.19
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 9245284.19 AND  l4_ul_goodput + l4_dw_goodput  < 9647253.07 THEN 9647253.07
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 9647253.07 AND  l4_ul_goodput + l4_dw_goodput  < 10049221.95 THEN 10049221.95
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 10049221.95 AND  l4_ul_goodput + l4_dw_goodput  < 10451190.83 THEN 10451190.83
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 10451190.83 AND  l4_ul_goodput + l4_dw_goodput  < 10853159.71 THEN 10853159.71
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 10853159.71 AND  l4_ul_goodput + l4_dw_goodput  < 11255128.58 THEN 11255128.58
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 11255128.58 AND  l4_ul_goodput + l4_dw_goodput  < 11657097.46 THEN 11657097.46
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 11657097.46 AND  l4_ul_goodput + l4_dw_goodput  < 12059066.34 THEN 12059066.34
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 12059066.34 AND  l4_ul_goodput + l4_dw_goodput  < 12461035.22 THEN 12461035.22
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 12461035.22 AND  l4_ul_goodput + l4_dw_goodput  < 12863004.1 THEN 12863004.1
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 12863004.1 AND  l4_ul_goodput + l4_dw_goodput  < 13264972.97 THEN 13264972.97
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 13264972.97 AND  l4_ul_goodput + l4_dw_goodput  < 13666941.85 THEN 13666941.85
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 13666941.85 AND  l4_ul_goodput + l4_dw_goodput  < 14068910.73 THEN 14068910.73
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 14068910.73 AND  l4_ul_goodput + l4_dw_goodput  < 14470879.61 THEN 14470879.61
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 14470879.61 AND  l4_ul_goodput + l4_dw_goodput  < 14872848.49 THEN 14872848.49
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 14872848.49 AND  l4_ul_goodput + l4_dw_goodput  < 15274817.36 THEN 15274817.36
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 15274817.36 AND  l4_ul_goodput + l4_dw_goodput  < 15676786.24 THEN 15676786.24
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 15676786.24 AND  l4_ul_goodput + l4_dw_goodput  < 16078755.12 THEN 16078755.12
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 16078755.12 AND  l4_ul_goodput + l4_dw_goodput  < 16480724.0 THEN 16480724.0
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 16480724.0 AND  l4_ul_goodput + l4_dw_goodput  < 16882692.88 THEN 16882692.88
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 16882692.88 AND  l4_ul_goodput + l4_dw_goodput  < 17284661.75 THEN 17284661.75
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 17284661.75 AND  l4_ul_goodput + l4_dw_goodput  < 17686630.63 THEN 17686630.63
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 17686630.63 AND  l4_ul_goodput + l4_dw_goodput  < 18088599.51 THEN 18088599.51
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 18088599.51 AND  l4_ul_goodput + l4_dw_goodput  < 18490568.39 THEN 18490568.39
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 18490568.39 AND  l4_ul_goodput + l4_dw_goodput  < 18892537.27 THEN 18892537.27
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 18892537.27 AND  l4_ul_goodput + l4_dw_goodput  < 19294506.14 THEN 19294506.14
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 19294506.14 AND  l4_ul_goodput + l4_dw_goodput  < 19696475.02 THEN 19696475.02
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 19696475.02 AND  l4_ul_goodput + l4_dw_goodput  < 20098443.9 THEN 20098443.9
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 20098443.9 AND  l4_ul_goodput + l4_dw_goodput  < 20500412.78 THEN 20500412.78
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 20500412.78 AND  l4_ul_goodput + l4_dw_goodput  < 20902381.66 THEN 20902381.66
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 20902381.66 AND  l4_ul_goodput + l4_dw_goodput  < 21304350.53 THEN 21304350.53
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 21304350.53 AND  l4_ul_goodput + l4_dw_goodput  < 21706319.41 THEN 21706319.41
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 21706319.41 AND  l4_ul_goodput + l4_dw_goodput  < 22108288.29 THEN 22108288.29
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 22108288.29 AND  l4_ul_goodput + l4_dw_goodput  < 22510257.17 THEN 22510257.17
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 22510257.17 AND  l4_ul_goodput + l4_dw_goodput  < 22912226.05 THEN 22912226.05
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 22912226.05 AND  l4_ul_goodput + l4_dw_goodput  < 23314194.92 THEN 23314194.92
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 23314194.92 AND  l4_ul_goodput + l4_dw_goodput  < 23716163.8 THEN 23716163.8
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 23716163.8 AND  l4_ul_goodput + l4_dw_goodput  < 24118132.68 THEN 24118132.68
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 24118132.68 AND  l4_ul_goodput + l4_dw_goodput  < 24520101.56 THEN 24520101.56
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 24520101.56 AND  l4_ul_goodput + l4_dw_goodput  < 24922070.44 THEN 24922070.44
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 24922070.44 AND  l4_ul_goodput + l4_dw_goodput  < 25324039.31 THEN 25324039.31
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 25324039.31 AND  l4_ul_goodput + l4_dw_goodput  < 25726008.19 THEN 25726008.19
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 25726008.19 AND  l4_ul_goodput + l4_dw_goodput  < 26127977.07 THEN 26127977.07
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 26127977.07 AND  l4_ul_goodput + l4_dw_goodput  < 26529945.95 THEN 26529945.95
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 26529945.95 AND  l4_ul_goodput + l4_dw_goodput  < 26931914.83 THEN 26931914.83
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 26931914.83 AND  l4_ul_goodput + l4_dw_goodput  < 27333883.7 THEN 27333883.7
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 27333883.7 AND  l4_ul_goodput + l4_dw_goodput  < 27735852.58 THEN 27735852.58
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 27735852.58 AND  l4_ul_goodput + l4_dw_goodput  < 28137821.46 THEN 28137821.46
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 28137821.46 AND  l4_ul_goodput + l4_dw_goodput  < 28539790.34 THEN 28539790.34
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 28539790.34 AND  l4_ul_goodput + l4_dw_goodput  < 28941759.22 THEN 28941759.22
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 28941759.22 AND  l4_ul_goodput + l4_dw_goodput  < 29343728.09 THEN 29343728.09
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 29343728.09 AND  l4_ul_goodput + l4_dw_goodput  < 29745696.97 THEN 29745696.97
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 29745696.97 AND  l4_ul_goodput + l4_dw_goodput  < 30147665.85 THEN 30147665.85
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 30147665.85 AND  l4_ul_goodput + l4_dw_goodput  < 30549634.73 THEN 30549634.73
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 30549634.73 AND  l4_ul_goodput + l4_dw_goodput  < 30951603.61 THEN 30951603.61
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 30951603.61 AND  l4_ul_goodput + l4_dw_goodput  < 31353572.48 THEN 31353572.48
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 31353572.48 AND  l4_ul_goodput + l4_dw_goodput  < 31755541.36 THEN 31755541.36
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 31755541.36 AND  l4_ul_goodput + l4_dw_goodput  < 32157510.24 THEN 32157510.24
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 32157510.24 AND  l4_ul_goodput + l4_dw_goodput  < 32559479.12 THEN 32559479.12
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 32559479.12 AND  l4_ul_goodput + l4_dw_goodput  < 32961448.0 THEN 32961448.0
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 32961448.0 AND  l4_ul_goodput + l4_dw_goodput  < 33363416.87 THEN 33363416.87
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 33363416.87 AND  l4_ul_goodput + l4_dw_goodput  < 33765385.75 THEN 33765385.75
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 33765385.75 AND  l4_ul_goodput + l4_dw_goodput  < 34167354.63 THEN 34167354.63
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 34167354.63 AND  l4_ul_goodput + l4_dw_goodput  < 34569323.51 THEN 34569323.51
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 34569323.51 AND  l4_ul_goodput + l4_dw_goodput  < 34971292.39 THEN 34971292.39
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 34971292.39 AND  l4_ul_goodput + l4_dw_goodput  < 35373261.26 THEN 35373261.26
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 35373261.26 AND  l4_ul_goodput + l4_dw_goodput  < 35775230.14 THEN 35775230.14
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 35775230.14 AND  l4_ul_goodput + l4_dw_goodput  < 36177199.02 THEN 36177199.02
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 36177199.02 AND  l4_ul_goodput + l4_dw_goodput  < 36579167.9 THEN 36579167.9
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 36579167.9 AND  l4_ul_goodput + l4_dw_goodput  < 36981136.78 THEN 36981136.78
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 36981136.78 AND  l4_ul_goodput + l4_dw_goodput  < 37383105.65 THEN 37383105.65
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 37383105.65 AND  l4_ul_goodput + l4_dw_goodput  < 37785074.53 THEN 37785074.53
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 37785074.53 AND  l4_ul_goodput + l4_dw_goodput  < 38187043.41 THEN 38187043.41
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 38187043.41 AND  l4_ul_goodput + l4_dw_goodput  < 38589012.29 THEN 38589012.29
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 38589012.29 AND  l4_ul_goodput + l4_dw_goodput  < 38990981.17 THEN 38990981.17
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 38990981.17 AND  l4_ul_goodput + l4_dw_goodput  < 39392950.04 THEN 39392950.04
 WHEN  l4_ul_goodput + l4_dw_goodput  >= 39392950.04 AND  l4_ul_goodput + l4_dw_goodput  < 39794918.92 THEN 39794918.92
 WHEN   l4_ul_goodput + l4_dw_goodput  >= 39794918.92 THEN 999999999
 ELSE NULL END as Score
from (
select msisdn, 
sum(l4_dw_goodput) as l4_dw_goodput,
sum(l4_ul_goodput) as l4_ul_goodput
from detail_ufdr_http_browsing_18530
where msisdn <>'' AND tethering_flag=1
group by msisdn
) as f
) as g
group by Score
order by Score asc
;

```

