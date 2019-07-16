

```python
import urllib
import json
from pprint import pprint
import requests
import pandas as pd
```


```python
base_url = "http://openapi.seoul.go.kr:8088"
ServiceKey = "76586f6f6964756435334763747a6a"
response_type = "json"
headers = {'content-type':'application/json;charset=utf-8'}
```


```python
def call_api(base_url, ServiceKey, response_type, service, start_index, end_index, api_name):
    url = '/'.join([base_url, ServiceKey, response_type, service, start_index, end_index])
    response=requests.get(url, headers=headers)
    result = response.json()
    data = result[api_name]['row']
    
    return data
```


```python
# def call_public_bicycle_rent_id_info():
#     api_name = "PublicBicycleRenTIdinfo"
#     service = "PublicBicycleRenTIdinfo"
#     index = [("1", "1000"),("1001", "2000")]
#     result = []
    
#     for start_index, end_index in index:
#         result.extend(call_api(base_url, ServiceKey, response_type, service, start_index, end_index, api_name))
        
#     return result
```


```python
# result = call_public_bicycle_rent_id_info()
# call_public_bicycle_rent_id_info = pd.DataFrame(result)
# call_public_bicycle_rent_id_info['datetime'] = pd.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
```


```python
# call_public_bicycle_rent_id_info
```

###### cycle Rent Use Time Info


```python
# def call_cycle_rent_use_time_info():
#     api_name = "cycleRentUseTimeInfo"
#     service = "cycleRentUseTimeInfo"
#     index = [("1", "1000")]
#     result = []
    
#     for start_index, end_index in index:
#         result.extend(call_api(base_url, ServiceKey, response_type, service, start_index, end_index, api_name))
        
#     return result
```


```python
# url = '/'.join([base_url, ServiceKey, response_type, "cycleRentUseTimeInfo", "1", "5"])
# response=requests.get(url, headers=headers)
# result = response.json()
# #data = result[api_name]['row']
```


```python
# result = call_cycle_rent_use_time_info()
```


```python
# call_cycle_rent_use_time_info_df = pd.DataFrame(result)
# call_cycle_rent_use_time_info_df['datetime'] = pd.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
```


```python
# call_cycle_rent_use_time_info_df
```

##### Rent Bike Status


```python
def call_rent_bike_status():
    api_name = "rentBikeStatus"
    service = "bikeList"
    index = [("1", "1000"), ("1001", "2000")]
    result = []
    
    for start_index, end_index in index:
        result.extend(call_api(base_url, ServiceKey, response_type, service, start_index, end_index, api_name))
        
    return result
```


```python
result = call_rent_bike_status()
```


```python
result
```




    [{'parkingBikeTotCnt': '6',
      'rackTotCnt': '5',
      'shared': '120',
      'stationId': 'ST-3',
      'stationLatitude': '37.549561',
      'stationLongitude': '126.905754',
      'stationName': '101. (구)합정동 주민센터'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '20',
      'shared': '20',
      'stationId': 'ST-4',
      'stationLatitude': '37.555649',
      'stationLongitude': '126.910629',
      'stationName': '102. 망원역 1번출구 앞'},
     {'parkingBikeTotCnt': '48',
      'rackTotCnt': '15',
      'shared': '320',
      'stationId': 'ST-1040',
      'stationLatitude': '37.549999',
      'stationLongitude': '127.174690',
      'stationName': '1023. 한국종합기술사옥 앞'},
     {'parkingBikeTotCnt': '35',
      'rackTotCnt': '10',
      'shared': '350',
      'stationId': 'ST-1041',
      'stationLatitude': '37.529251',
      'stationLongitude': '127.123108',
      'stationName': '1024.  강동구청 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-1042',
      'stationLatitude': '37.546841',
      'stationLongitude': '127.172516',
      'stationName': '1025. 상일초등학교'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '14',
      'shared': '43',
      'stationId': 'ST-1043',
      'stationLatitude': '37.546631',
      'stationLongitude': '127.155884',
      'stationName': '1026. 대명초교 입구 교차로'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '20',
      'shared': '35',
      'stationId': 'ST-1044',
      'stationLatitude': '37.535999',
      'stationLongitude': '127.147697',
      'stationName': '1027. 프라자 아파트 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1045',
      'stationLatitude': '37.533100',
      'stationLongitude': '127.122780',
      'stationName': '1028. 포레스 주상복합 빌딩'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1046',
      'stationLatitude': '37.536541',
      'stationLongitude': '127.125397',
      'stationName': '1029. 롯데 시네마'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '15',
      'shared': '80',
      'stationId': 'ST-1047',
      'stationLatitude': '37.527061',
      'stationLongitude': '127.122070',
      'stationName': '1030. 미호 플랜트 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '15',
      'shared': '107',
      'stationId': 'ST-1048',
      'stationLatitude': '37.555851',
      'stationLongitude': '127.129898',
      'stationName': '1031. 암사동 CBIS'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-1049',
      'stationLatitude': '37.556728',
      'stationLongitude': '127.136208',
      'stationName': '1032. 선사고등학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1050',
      'stationLatitude': '37.557991',
      'stationLongitude': '127.144707',
      'stationName': '1033. 고덕동 아남아파트'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1051',
      'stationLatitude': '37.561909',
      'stationLongitude': '127.150749',
      'stationName': '1034. 고덕동 래미안 힐스테이트'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1052',
      'stationLatitude': '37.555016',
      'stationLongitude': '127.155273',
      'stationName': '1035. 고덕역 4번출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1053',
      'stationLatitude': '37.551998',
      'stationLongitude': '127.153297',
      'stationName': '1036. 고덕동 주양쇼핑'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1054',
      'stationLatitude': '37.562588',
      'stationLongitude': '127.177612',
      'stationName': '1037. 강일 6단지'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1055',
      'stationLatitude': '37.568668',
      'stationLongitude': '127.174797',
      'stationName': '1038. 강일 다솜 어린이 공원'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '7',
      'shared': '200',
      'stationId': 'ST-1056',
      'stationLatitude': '37.561279',
      'stationLongitude': '127.167801',
      'stationName': '1039. 고덕초등학교'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1058',
      'stationLatitude': '37.559196',
      'stationLongitude': '127.153297',
      'stationName': '1041. 묘곡초등학교'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1059',
      'stationLatitude': '37.568562',
      'stationLongitude': '127.177002',
      'stationName': '1042. 강일 2.5단지 사이'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '15',
      'shared': '127',
      'stationId': 'ST-1061',
      'stationLatitude': '37.545399',
      'stationLongitude': '127.142601',
      'stationName': '1044. 굽은다리역'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1369',
      'stationLatitude': '37.536381',
      'stationLongitude': '127.137253',
      'stationName': '1047. 건강보험 강동지사kt'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1370',
      'stationLatitude': '37.531013',
      'stationLongitude': '127.142365',
      'stationName': '1048. 동부기업(둔촌동)'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1371',
      'stationLatitude': '37.561180',
      'stationLongitude': '127.180267',
      'stationName': '1049. 강일동 10단지 아파트'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '15',
      'shared': '127',
      'stationId': 'ST-1420',
      'stationLatitude': '37.526695',
      'stationLongitude': '127.135529',
      'stationName': '1050.  둔촌역 3번 출입구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1421',
      'stationLatitude': '37.554829',
      'stationLongitude': '127.137321',
      'stationName': '1051. 양지시장 (용성약국앞) 입구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1593',
      'stationLatitude': '37.556469',
      'stationLongitude': '127.156822',
      'stationName': '1052. 리싸이클시티'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1594',
      'stationLatitude': '37.562538',
      'stationLongitude': '127.164528',
      'stationName': '1053. 동명근린공원 진입로 (아리수로)'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1595',
      'stationLatitude': '37.560009',
      'stationLongitude': '127.169579',
      'stationName': '1054. 말우물 어린이 공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1597',
      'stationLatitude': '37.563332',
      'stationLongitude': '127.179092',
      'stationName': '1056. 강일리엔파크 7~11단지'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-1598',
      'stationLatitude': '37.555790',
      'stationLongitude': '127.173813',
      'stationName': '1057. 능골근린공원'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '12',
      'shared': '83',
      'stationId': 'ST-1623',
      'stationLatitude': '37.553471',
      'stationLongitude': '127.165001',
      'stationName': '1058. 고덕숲 아이파크 1'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1626',
      'stationLatitude': '37.538181',
      'stationLongitude': '127.131752',
      'stationName': '1059. 레미안 강동팰리스(102동)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1620',
      'stationLatitude': '37.544659',
      'stationLongitude': '127.132637',
      'stationName': '1060. 천일초교 사거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1621',
      'stationLatitude': '37.546928',
      'stationLongitude': '127.134621',
      'stationName': '1061. 천호초교 입구 사거리(일주빌딩)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1622',
      'stationLatitude': '37.551079',
      'stationLongitude': '127.162621',
      'stationName': '1062. 고덕숲 아이파크 2'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-10',
      'stationLatitude': '37.552746',
      'stationLongitude': '126.918617',
      'stationName': '108. 서교동 사거리'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-11',
      'stationLatitude': '37.547691',
      'stationLongitude': '126.919983',
      'stationName': '109. 제일빌딩 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '20',
      'shared': '25',
      'stationId': 'ST-13',
      'stationLatitude': '37.568199',
      'stationLongitude': '126.917847',
      'stationName': '110. 사천교'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-15',
      'stationLatitude': '37.547871',
      'stationLongitude': '126.923531',
      'stationName': '111. 상수역 2번출구 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-16',
      'stationLatitude': '37.549202',
      'stationLongitude': '126.923203',
      'stationName': '112. 극동방송국 앞'},
     {'parkingBikeTotCnt': '76',
      'rackTotCnt': '25',
      'shared': '304',
      'stationId': 'ST-18',
      'stationLatitude': '37.557499',
      'stationLongitude': '126.923805',
      'stationName': '113. 홍대입구역 2번출구 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-20',
      'stationLatitude': '37.557060',
      'stationLongitude': '126.924423',
      'stationName': '114. 홍대입구역 8번출구 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-12',
      'stationLatitude': '37.558933',
      'stationLongitude': '126.927116',
      'stationName': '115. 사루비아 빌딩 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1062',
      'stationLatitude': '37.561550',
      'stationLongitude': '126.810478',
      'stationName': '1150. 송정역 1번출구'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '25',
      'shared': '64',
      'stationId': 'ST-1063',
      'stationLatitude': '37.560234',
      'stationLongitude': '126.823471',
      'stationName': '1151. 마곡역1번출구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1064',
      'stationLatitude': '37.558666',
      'stationLongitude': '126.826614',
      'stationName': '1152. 마곡역교차로'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1065',
      'stationLatitude': '37.558891',
      'stationLongitude': '126.837219',
      'stationName': '1153. 발산역 1번, 9번 인근 대여소'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1067',
      'stationLatitude': '37.569260',
      'stationLongitude': '126.848419',
      'stationName': '1155. 기쁜우리복지관'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1069',
      'stationLatitude': '37.550659',
      'stationLongitude': '126.849770',
      'stationName': '1157. 강서구청'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-1249',
      'stationLatitude': '37.561035',
      'stationLongitude': '126.854813',
      'stationName': '1158. 가양역 8번출구'},
     {'parkingBikeTotCnt': '34',
      'rackTotCnt': '20',
      'shared': '170',
      'stationId': 'ST-1250',
      'stationLatitude': '37.565853',
      'stationLongitude': '126.846596',
      'stationName': '1159. 서서울모터리움앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '5',
      'shared': '0',
      'stationId': 'ST-14',
      'stationLatitude': '37.564541',
      'stationLongitude': '126.927071',
      'stationName': '116. 일진아이윌아파트 옆'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '20',
      'shared': '30',
      'stationId': 'ST-1251',
      'stationLatitude': '37.567680',
      'stationLongitude': '126.840897',
      'stationName': '1160. 양천향교역 7번출구앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1252',
      'stationLatitude': '37.549694',
      'stationLongitude': '126.819664',
      'stationName': '1161. 강서면허시험장앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1253',
      'stationLatitude': '37.562679',
      'stationLongitude': '126.820473',
      'stationName': '1162. 공항초등학교건너편'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1254',
      'stationLatitude': '37.570499',
      'stationLongitude': '126.820084',
      'stationName': '1163. 방화동강서기동대앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1338',
      'stationLatitude': '37.568447',
      'stationLongitude': '126.821648',
      'stationName': '1165. 마곡중학교 후문'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1351',
      'stationLatitude': '37.562569',
      'stationLongitude': '126.842461',
      'stationName': '1166. 강서구립등빛도서관'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-1352',
      'stationLatitude': '37.553467',
      'stationLongitude': '126.825928',
      'stationName': '1167. 마곡수명산파크3단지 교차로'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1402',
      'stationLatitude': '37.560226',
      'stationLongitude': '126.819069',
      'stationName': '1168. 마곡엠밸리10단지 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1506',
      'stationLatitude': '37.547199',
      'stationLongitude': '126.874489',
      'stationName': '1169. 염창역 1번 출구'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '25',
      'shared': '56',
      'stationId': 'ST-17',
      'stationLatitude': '37.591160',
      'stationLongitude': '126.941330',
      'stationName': '117. 홍은사거리'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '11',
      'shared': '27',
      'stationId': 'ST-1507',
      'stationLatitude': '37.549179',
      'stationLongitude': '126.868797',
      'stationName': '1170. 강서구보건소 (삼성디지털 프라자)'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '8',
      'shared': '63',
      'stationId': 'ST-1508',
      'stationLatitude': '37.550049',
      'stationLongitude': '126.873161',
      'stationName': '1171. 염창동 새마을금고 건너편 (모닝글로리)'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-1509',
      'stationLatitude': '37.561249',
      'stationLongitude': '126.860580',
      'stationName': '1172. 가양3동 주민센터'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1510',
      'stationLatitude': '37.556259',
      'stationLongitude': '126.853317',
      'stationName': '1173. 강서구청사거리(SH타워)'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '9',
      'shared': '67',
      'stationId': 'ST-1511',
      'stationLatitude': '37.556599',
      'stationLongitude': '126.851471',
      'stationName': '1174. 강서구청사거리(부민병원)'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-1512',
      'stationLatitude': '37.554379',
      'stationLongitude': '126.857536',
      'stationName': '1175. 대한항공 인력개발센터'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1514',
      'stationLatitude': '37.550110',
      'stationLongitude': '126.823677',
      'stationName': '1177. 수명중․고교'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1515',
      'stationLatitude': '37.572472',
      'stationLongitude': '126.806168',
      'stationName': '1178. 개화산역 2번 출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-19',
      'stationLatitude': '37.547733',
      'stationLongitude': '126.931763',
      'stationName': '118. 광흥창역 2번출구 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1517',
      'stationLatitude': '37.557468',
      'stationLongitude': '126.829720',
      'stationName': '1180. 마곡엠밸리 15단지(1502동) 건너편'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1518',
      'stationLatitude': '37.551044',
      'stationLongitude': '126.818497',
      'stationName': '1181. 농수산식품공사 (강서지사)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1519',
      'stationLatitude': '37.556877',
      'stationLongitude': '126.848808',
      'stationName': '1182. KBS 스포츠월드'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1520',
      'stationLatitude': '37.548321',
      'stationLongitude': '126.853401',
      'stationName': '1183. KC 대학교'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1645',
      'stationLatitude': '37.556450',
      'stationLongitude': '126.815979',
      'stationName': '1184. 마곡13단지'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1646',
      'stationLatitude': '37.562901',
      'stationLongitude': '126.849472',
      'stationName': '1185. 등촌9단지'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1647',
      'stationLatitude': '37.554729',
      'stationLongitude': '126.816093',
      'stationName': '1186. 송정중학교'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-1676',
      'stationLatitude': '37.553020',
      'stationLongitude': '126.818367',
      'stationName': '1187. 강서수산물도매시장'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '8',
      'shared': '100',
      'stationId': 'ST-1708',
      'stationLatitude': '37.571381',
      'stationLongitude': '126.828339',
      'stationName': '1188. 롯데중앙연구소'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-21',
      'stationLatitude': '37.545284',
      'stationLongitude': '126.931053',
      'stationName': '119. 서강나루 공원'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1709',
      'stationLatitude': '37.560501',
      'stationLongitude': '126.826653',
      'stationName': '1190. 마곡역 교차로(2번출구)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '9',
      'shared': '22',
      'stationId': 'ST-1689',
      'stationLatitude': '37.560242',
      'stationLongitude': '126.827164',
      'stationName': '1191. 마곡역 교차로(NH농협)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1710',
      'stationLatitude': '37.555538',
      'stationLongitude': '126.826759',
      'stationName': '1192. 마곡수명산파크 209동 건너편'},
     {'parkingBikeTotCnt': '32',
      'rackTotCnt': '15',
      'shared': '213',
      'stationId': 'ST-1688',
      'stationLatitude': '37.559471',
      'stationLongitude': '126.832077',
      'stationName': '1193. 마곡센트럴타워 1차'},
     {'parkingBikeTotCnt': '34',
      'rackTotCnt': '10',
      'shared': '340',
      'stationId': 'ST-1711',
      'stationLatitude': '37.563301',
      'stationLongitude': '126.836823',
      'stationName': '1194. 센서텍㈜'},
     {'parkingBikeTotCnt': '93',
      'rackTotCnt': '20',
      'shared': '465',
      'stationId': 'ST-1712',
      'stationLatitude': '37.564129',
      'stationLongitude': '126.834312',
      'stationName': '1195. 코오롱One&Only타워'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '15',
      'shared': '127',
      'stationId': 'ST-1713',
      'stationLatitude': '37.568241',
      'stationLongitude': '126.835831',
      'stationName': '1196. 서울식물원(문화센터) 건너편'},
     {'parkingBikeTotCnt': '30',
      'rackTotCnt': '20',
      'shared': '150',
      'stationId': 'ST-1714',
      'stationLatitude': '37.560242',
      'stationLongitude': '126.835808',
      'stationName': '1197. 엘펠리체 호텔 건너편'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '20',
      'shared': '80',
      'stationId': 'ST-1715',
      'stationLatitude': '37.562550',
      'stationLongitude': '126.827438',
      'stationName': '1198. LG 사이언스파크'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '13',
      'shared': '77',
      'stationId': 'ST-1694',
      'stationLatitude': '37.547821',
      'stationLongitude': '126.836128',
      'stationName': '1199. 우장산역 3번출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '5',
      'shared': '80',
      'stationId': 'ST-22',
      'stationLatitude': '37.545242',
      'stationLongitude': '126.934113',
      'stationName': '120. 신수동 사거리'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1695',
      'stationLatitude': '37.578449',
      'stationLongitude': '126.798973',
      'stationName': '1200. 개화광역환승센터'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-23',
      'stationLatitude': '37.549767',
      'stationLongitude': '126.933174',
      'stationName': '121. 마포소방서 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-24',
      'stationLatitude': '37.547459',
      'stationLongitude': '126.938377',
      'stationName': '122. 신성기사식당 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-25',
      'stationLatitude': '37.594330',
      'stationLongitude': '126.947388',
      'stationName': '123. 문화촌 공원'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-26',
      'stationLatitude': '37.551140',
      'stationLongitude': '126.936989',
      'stationName': '124. 서강대 정문 건너편'},
     {'parkingBikeTotCnt': '26',
      'rackTotCnt': '15',
      'shared': '173',
      'stationId': 'ST-27',
      'stationLatitude': '37.549484',
      'stationLongitude': '126.938950',
      'stationName': '125. 서강대 남문 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1070',
      'stationLatitude': '37.505932',
      'stationLongitude': '127.107750',
      'stationName': '1251. 석촌역 2번출구'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1072',
      'stationLatitude': '37.501652',
      'stationLongitude': '127.128181',
      'stationName': '1253. 오금역 3번 출구 뒤'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1075',
      'stationLatitude': '37.491131',
      'stationLongitude': '127.125809',
      'stationName': '1256. 문정현대아파트 교차로'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1076',
      'stationLatitude': '37.492100',
      'stationLongitude': '127.117752',
      'stationName': '1257. 가락시장역 롯데마트앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1077',
      'stationLatitude': '37.493198',
      'stationLongitude': '127.128998',
      'stationName': '1258. 가락미륭아파트 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-1078',
      'stationLatitude': '37.508984',
      'stationLongitude': '127.126595',
      'stationName': '1259. 방이역 1번출구'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '20',
      'shared': '85',
      'stationId': 'ST-28',
      'stationLatitude': '37.550411',
      'stationLongitude': '126.943848',
      'stationName': '126. 서강대 후문 옆'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1079',
      'stationLatitude': '37.506302',
      'stationLongitude': '127.121399',
      'stationName': '1260. 방이동 한양3차아파트 옆'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1081',
      'stationLatitude': '37.505802',
      'stationLongitude': '127.109718',
      'stationName': '1262. 송파여성문화회관 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1082',
      'stationLatitude': '37.480541',
      'stationLongitude': '127.137016',
      'stationName': '1263. 장지공영차고지'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1083',
      'stationLatitude': '37.538582',
      'stationLongitude': '127.122803',
      'stationName': '1264. 천호역 10번 출구 앞'},
     {'parkingBikeTotCnt': '27',
      'rackTotCnt': '10',
      'shared': '270',
      'stationId': 'ST-1084',
      'stationLatitude': '37.485989',
      'stationLongitude': '127.124763',
      'stationName': '1265. 문정동 근린공원'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1085',
      'stationLatitude': '37.478809',
      'stationLongitude': '127.120003',
      'stationName': '1266. 문정동 글샘 공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1086',
      'stationLatitude': '37.514240',
      'stationLongitude': '127.123070',
      'stationName': '1267. 올림픽공원 남2문 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-1087',
      'stationLatitude': '37.517288',
      'stationLongitude': '127.114197',
      'stationName': '1268. 몽촌토성역 1번출구 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1088',
      'stationLatitude': '37.511944',
      'stationLongitude': '127.091217',
      'stationName': '1269. 리센츠아파트 '},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-29',
      'stationLatitude': '37.553520',
      'stationLongitude': '126.936951',
      'stationName': '127. 현대벤처빌 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1089',
      'stationLatitude': '37.499985',
      'stationLongitude': '127.135391',
      'stationName': '1271. 송파도서관'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1092',
      'stationLatitude': '37.532848',
      'stationLongitude': '127.121048',
      'stationName': '1274. 영파여고 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-1367',
      'stationLatitude': '37.504589',
      'stationLongitude': '127.139366',
      'stationName': '1275. 거여초등학교 옆'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '8',
      'shared': '188',
      'stationId': 'ST-1408',
      'stationLatitude': '37.503757',
      'stationLongitude': '127.137093',
      'stationName': '1277. 오금동 송파 참병원'},
     {'parkingBikeTotCnt': '24',
      'rackTotCnt': '10',
      'shared': '240',
      'stationId': 'ST-1409',
      'stationLatitude': '37.515831',
      'stationLongitude': '127.106796',
      'stationName': '1278. 송파구청 교차로'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1410',
      'stationLatitude': '37.497517',
      'stationLongitude': '127.154678',
      'stationName': '1279. 마천금호어울림 1차아파트 건너편'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-30',
      'stationLatitude': '37.555496',
      'stationLongitude': '126.936340',
      'stationName': '128. 신촌역(2호선) 1번출구 옆'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1411',
      'stationLatitude': '37.495659',
      'stationLongitude': '127.157173',
      'stationName': '1280. 송파파크데일 2단지입구 앞 주차장'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1413',
      'stationLatitude': '37.499874',
      'stationLongitude': '127.141479',
      'stationName': '1282. 송파소방서 맞은편(성내4교)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1414',
      'stationLatitude': '37.505455',
      'stationLongitude': '127.131752',
      'stationName': '1283. 오금공원 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1416',
      'stationLatitude': '37.477470',
      'stationLongitude': '127.144592',
      'stationName': '1285. 위례별 유치원 뒤'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1417',
      'stationLatitude': '37.474377',
      'stationLongitude': '127.140671',
      'stationName': '1286. 위례중앙푸르지오 1단지 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1418',
      'stationLatitude': '37.477531',
      'stationLongitude': '127.141518',
      'stationName': '1287. 위례아이파크 101동 맞은편'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1419',
      'stationLatitude': '37.487999',
      'stationLongitude': '127.131088',
      'stationName': '1288. 문정중교 사거리'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1422',
      'stationLatitude': '37.531471',
      'stationLongitude': '127.111092',
      'stationName': '1289. 풍납동 자전거보관소'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-31',
      'stationLatitude': '37.555054',
      'stationLongitude': '126.937569',
      'stationName': '129. 신촌역(2호선) 6번출구 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1579',
      'stationLatitude': '37.474659',
      'stationLongitude': '127.137718',
      'stationName': '1290. 위례송파꿈에그린아파트24단지 앞 성벽 다리 밑'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1580',
      'stationLatitude': '37.521938',
      'stationLongitude': '127.131866',
      'stationName': '1291. 서울체육고등학교 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1582',
      'stationLatitude': '37.506561',
      'stationLongitude': '127.096558',
      'stationName': '1293. 석촌호교차로 (스타벅스 앞)'},
     {'parkingBikeTotCnt': '22',
      'rackTotCnt': '20',
      'shared': '110',
      'stationId': 'ST-1584',
      'stationLatitude': '37.513962',
      'stationLongitude': '127.100304',
      'stationName': '1295. 잠실역 8번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1585',
      'stationLatitude': '37.508678',
      'stationLongitude': '127.103432',
      'stationName': '1296. 석촌호수교차로 (송파나루근린공원 앞)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1586',
      'stationLatitude': '37.509201',
      'stationLongitude': '127.104118',
      'stationName': '1297. 석촌호수교차로(동호 팔각정 앞)'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1588',
      'stationLatitude': '37.519878',
      'stationLongitude': '127.136711',
      'stationName': '1299. 송파소방서 (방이119안전센터)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-32',
      'stationLatitude': '37.554859',
      'stationLongitude': '126.936157',
      'stationName': '130. 신촌역(2호선) 7번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1589',
      'stationLatitude': '37.506939',
      'stationLongitude': '127.139221',
      'stationName': '1300. 오륜사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '23',
      'shared': '17',
      'stationId': 'ST-33',
      'stationLatitude': '37.584171',
      'stationLongitude': '126.911102',
      'stationName': '131. 증산2교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-35',
      'stationLatitude': '37.582031',
      'stationLongitude': '126.908997',
      'stationName': '133. 해담는다리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '20',
      'shared': '10',
      'stationId': 'ST-1200',
      'stationLatitude': '37.591251',
      'stationLongitude': '127.014008',
      'stationName': '1336. 성북3교 위'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1201',
      'stationLatitude': '37.590382',
      'stationLongitude': '127.017136',
      'stationName': '1337. 돈암성당 옆'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-1202',
      'stationLatitude': '37.586899',
      'stationLongitude': '127.020752',
      'stationName': '1338. 용문2교 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-1203',
      'stationLatitude': '37.610569',
      'stationLongitude': '127.033508',
      'stationName': '1339. 삼성전자서비스 성북센터'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '8',
      'shared': '88',
      'stationId': 'ST-36',
      'stationLatitude': '37.557892',
      'stationLongitude': '126.938080',
      'stationName': '134. 연세로 명물길'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '8',
      'shared': '63',
      'stationId': 'ST-1204',
      'stationLatitude': '37.619560',
      'stationLongitude': '127.053802',
      'stationName': '1340. 광운초등학교 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1206',
      'stationLatitude': '37.592617',
      'stationLongitude': '126.997932',
      'stationName': '1342. 성북쉼터 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1207',
      'stationLatitude': '37.589249',
      'stationLongitude': '127.007378',
      'stationName': '1343. 한성대7번출구 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1208',
      'stationLatitude': '37.600288',
      'stationLongitude': '127.013702',
      'stationName': '1344. 아리랑시네센터 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1210',
      'stationLatitude': '37.608978',
      'stationLongitude': '127.020248',
      'stationName': '1346. 길음8골어린이공원 옆'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '12',
      'shared': '133',
      'stationId': 'ST-1212',
      'stationLatitude': '37.604752',
      'stationLongitude': '127.022758',
      'stationName': '1348. 성북제일새마을금고 본점 앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1213',
      'stationLatitude': '37.623829',
      'stationLongitude': '127.050201',
      'stationName': '1349. 월계2교 버스정류장 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-37',
      'stationLatitude': '37.559101',
      'stationLongitude': '126.939178',
      'stationName': '135. 명물길 원형무대 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1215',
      'stationLatitude': '37.579449',
      'stationLongitude': '127.024193',
      'stationName': '1351. 안암2교 옆'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '8',
      'shared': '38',
      'stationId': 'ST-1216',
      'stationLatitude': '37.583881',
      'stationLongitude': '127.017097',
      'stationName': '1352. e 편한세상 보문아파트 내'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '8',
      'shared': '63',
      'stationId': 'ST-1217',
      'stationLatitude': '37.600830',
      'stationLongitude': '127.023552',
      'stationName': '1353. 금호어울림센터힐 내'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1317',
      'stationLatitude': '37.590714',
      'stationLongitude': '127.036194',
      'stationName': '1354. 고려대학교 2번출구'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '20',
      'shared': '65',
      'stationId': 'ST-1347',
      'stationLatitude': '37.588699',
      'stationLongitude': '127.018913',
      'stationName': '1355. 보문2교'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '20',
      'shared': '100',
      'stationId': 'ST-1383',
      'stationLatitude': '37.612072',
      'stationLongitude': '127.008133',
      'stationName': '1357. 북한산보국문역'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '7',
      'shared': '86',
      'stationId': 'ST-1384',
      'stationLatitude': '37.604790',
      'stationLongitude': '127.010582',
      'stationName': '1358. 정릉도서관 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '20',
      'shared': '25',
      'stationId': 'ST-1385',
      'stationLatitude': '37.619801',
      'stationLongitude': '127.045097',
      'stationName': '1359. 장위뉴타운 꿈에 숲 코오롱 하늘채 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '7',
      'shared': '14',
      'stationId': 'ST-38',
      'stationLatitude': '37.556004',
      'stationLongitude': '126.942299',
      'stationName': '136. 대흥동 주민센터'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1386',
      'stationLatitude': '37.603096',
      'stationLongitude': '127.013504',
      'stationName': '1360. 정릉역'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1424',
      'stationLatitude': '37.592842',
      'stationLongitude': '127.002121',
      'stationName': '1361. 홍익중고 입구'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1454',
      'stationLatitude': '37.585098',
      'stationLongitude': '127.019676',
      'stationName': '1362. 보문역6번출구 앞'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '15',
      'shared': '133',
      'stationId': 'ST-1455',
      'stationLatitude': '37.583752',
      'stationLongitude': '127.021950',
      'stationName': '1363. 보문4교 인근'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1456',
      'stationLatitude': '37.590172',
      'stationLongitude': '127.004089',
      'stationName': '1364. 성북동 치안센터 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1457',
      'stationLatitude': '37.593361',
      'stationLongitude': '126.999092',
      'stationName': '1365. 선잠단지 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1458',
      'stationLatitude': '37.599720',
      'stationLongitude': '127.040382',
      'stationName': '1366. 일신초등학교 옆'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-1459',
      'stationLatitude': '37.603512',
      'stationLongitude': '127.022560',
      'stationName': '1367. 길음문화복합미디어센터'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1460',
      'stationLatitude': '37.591480',
      'stationLongitude': '127.020103',
      'stationName': '1368. 성신여대입구 교차로'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1633',
      'stationLatitude': '37.609131',
      'stationLongitude': '127.030029',
      'stationName': '1369. 미아사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-39',
      'stationLatitude': '37.556812',
      'stationLongitude': '126.943184',
      'stationName': '137. NH농협 신촌지점 앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '20',
      'shared': '65',
      'stationId': 'ST-1634',
      'stationLatitude': '37.594540',
      'stationLongitude': '126.995209',
      'stationName': '1370. 복자사랑 피정의 집'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1636',
      'stationLatitude': '37.586445',
      'stationLongitude': '127.031601',
      'stationName': '1372. KEB은행 고대점'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '8',
      'shared': '113',
      'stationId': 'ST-1637',
      'stationLatitude': '37.602291',
      'stationLongitude': '127.038979',
      'stationName': '1373. 성북구보건소 건너편'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '20',
      'shared': '90',
      'stationId': 'ST-1723',
      'stationLatitude': '37.603909',
      'stationLongitude': '127.037376',
      'stationName': '1375. 생명의 전화 종합복지관 앞 교차로'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '7',
      'shared': '129',
      'stationId': 'ST-1745',
      'stationLatitude': '37.597321',
      'stationLongitude': '127.043808',
      'stationName': '1376. 한국과학기술연구원 중문'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1746',
      'stationLatitude': '37.603958',
      'stationLongitude': '127.045341',
      'stationName': '1377. 한국과학기술연구원 북문'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-40',
      'stationLatitude': '37.559177',
      'stationLongitude': '126.934525',
      'stationName': '138. 신촌동 제1공영주차장 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '13',
      'shared': '92',
      'stationId': 'ST-43',
      'stationLatitude': '37.559795',
      'stationLongitude': '126.934479',
      'stationName': '139. 연세대 정문 건너편'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '20',
      'shared': '115',
      'stationId': 'ST-41',
      'stationLatitude': '37.560009',
      'stationLongitude': '126.940735',
      'stationName': '140. 이화여대 후문'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '20',
      'shared': '45',
      'stationId': 'ST-42',
      'stationLatitude': '37.562382',
      'stationLongitude': '126.932648',
      'stationName': '141. 연대 대운동장 옆'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '11',
      'shared': '45',
      'stationId': 'ST-200',
      'stationLatitude': '37.557201',
      'stationLongitude': '126.955666',
      'stationName': '142. 아현역 4번출구 앞'},
     {'parkingBikeTotCnt': '22',
      'rackTotCnt': '9',
      'shared': '244',
      'stationId': 'ST-201',
      'stationLatitude': '37.544579',
      'stationLongitude': '126.950218',
      'stationName': '143. 공덕역 2번출구'},
     {'parkingBikeTotCnt': '29',
      'rackTotCnt': '10',
      'shared': '290',
      'stationId': 'ST-202',
      'stationLatitude': '37.543579',
      'stationLongitude': '126.951324',
      'stationName': '144. 공덕역 8번출구'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '8',
      'shared': '175',
      'stationId': 'ST-1093',
      'stationLatitude': '37.598591',
      'stationLongitude': '127.079819',
      'stationName': '1442. (구)신한은행 중랑교지점'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1094',
      'stationLatitude': '37.595520',
      'stationLongitude': '127.098778',
      'stationName': '1443. 구립망우청소년독서실'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-1095',
      'stationLatitude': '37.574028',
      'stationLongitude': '127.080544',
      'stationName': '1444. 면목4치안센터'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-1096',
      'stationLatitude': '37.579941',
      'stationLongitude': '127.079399',
      'stationName': '1445. 용마지구대'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1097',
      'stationLatitude': '37.591301',
      'stationLongitude': '127.080330',
      'stationName': '1446. 중랑전화국 교차로'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1098',
      'stationLatitude': '37.588902',
      'stationLongitude': '127.087280',
      'stationName': '1447. 면목역 3번출구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-1099',
      'stationLatitude': '37.597321',
      'stationLongitude': '127.089798',
      'stationName': '1448. 코스트코 상봉점'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-1332',
      'stationLatitude': '37.596558',
      'stationLongitude': '127.085838',
      'stationName': '1449. 상봉역 1번출구'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '9',
      'shared': '78',
      'stationId': 'ST-203',
      'stationLatitude': '37.544250',
      'stationLongitude': '126.951637',
      'stationName': '145. 공덕역 5번출구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1333',
      'stationLatitude': '37.619625',
      'stationLongitude': '127.085014',
      'stationName': '1450. 화랑대역 7번출구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1334',
      'stationLatitude': '37.592758',
      'stationLongitude': '127.072670',
      'stationName': '1451. 중랑세무서'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-1335',
      'stationLatitude': '37.585655',
      'stationLongitude': '127.075050',
      'stationName': '1452. 겸재교 진입부'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '9',
      'shared': '100',
      'stationId': 'ST-1345',
      'stationLatitude': '37.604603',
      'stationLongitude': '127.109253',
      'stationName': '1453. 중랑캠핑숲'},
     {'parkingBikeTotCnt': '25',
      'rackTotCnt': '10',
      'shared': '250',
      'stationId': 'ST-1346',
      'stationLatitude': '37.607349',
      'stationLongitude': '127.078590',
      'stationName': '1454. 한국전력공사(동대문 중랑지사)'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1375',
      'stationLatitude': '37.596329',
      'stationLongitude': '127.085899',
      'stationName': '1455. 상봉역 2번 출구'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1380',
      'stationLatitude': '37.595112',
      'stationLongitude': '127.100327',
      'stationName': '1456. 상아빌딩(우림시장 교차로)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1381',
      'stationLatitude': '37.589760',
      'stationLongitude': '127.093239',
      'stationName': '1457. 동원사거리'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '9',
      'shared': '200',
      'stationId': 'ST-1451',
      'stationLatitude': '37.597340',
      'stationLongitude': '127.093086',
      'stationName': '1458. 상봉터미널2'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1452',
      'stationLatitude': '37.580349',
      'stationLongitude': '127.092651',
      'stationName': '1459. 용마한신아파트사거리'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '12',
      'shared': '192',
      'stationId': 'ST-204',
      'stationLatitude': '37.539936',
      'stationLongitude': '126.945824',
      'stationName': '146. 마포역 2번출구 뒤'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '7',
      'shared': '71',
      'stationId': 'ST-205',
      'stationLatitude': '37.539272',
      'stationLongitude': '126.945915',
      'stationName': '147. 마포역 4번출구 뒤'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '11',
      'shared': '100',
      'stationId': 'ST-206',
      'stationLatitude': '37.542347',
      'stationLongitude': '126.943024',
      'stationName': '148. 용강동 주민센터 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-207',
      'stationLatitude': '37.552956',
      'stationLongitude': '126.934341',
      'stationName': '150. 서강대역 2번출구 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-208',
      'stationLatitude': '37.555687',
      'stationLongitude': '126.905548',
      'stationName': '151. 망원1동주민센터'},
     {'parkingBikeTotCnt': '30',
      'rackTotCnt': '30',
      'shared': '100',
      'stationId': 'ST-209',
      'stationLatitude': '37.556610',
      'stationLongitude': '126.898018',
      'stationName': '152. 마포구민체육센터 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1100',
      'stationLatitude': '37.641739',
      'stationLongitude': '127.024628',
      'stationName': '1526. 수유동 채선당앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1101',
      'stationLatitude': '37.627335',
      'stationLongitude': '127.026054',
      'stationName': '1527. 미아역 1번 출구 뒤'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1102',
      'stationLatitude': '37.615036',
      'stationLongitude': '127.020699',
      'stationName': '1528. 삼각산동 주민센터'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1103',
      'stationLatitude': '37.630180',
      'stationLongitude': '127.024910',
      'stationName': '1529. 미아동 한국전력공사'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '12',
      'shared': '83',
      'stationId': 'ST-210',
      'stationLatitude': '37.564697',
      'stationLongitude': '126.912613',
      'stationName': '153. 성산2교 사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1104',
      'stationLatitude': '37.643551',
      'stationLongitude': '127.022346',
      'stationName': '1530. 광산사거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1105',
      'stationLatitude': '37.613956',
      'stationLongitude': '127.030251',
      'stationName': '1531. 미아사거리 1번 출구'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1106',
      'stationLatitude': '37.626354',
      'stationLongitude': '127.047447',
      'stationName': '1532. 번3동 주민센터 교차로'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '10',
      'shared': '170',
      'stationId': 'ST-1107',
      'stationLatitude': '37.629917',
      'stationLongitude': '127.040916',
      'stationName': '1533. 번동 주공3, 4단지 교차로'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1108',
      'stationLatitude': '37.619637',
      'stationLongitude': '127.044533',
      'stationName': '1534. 북서울 꿈의 숲 동문'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1109',
      'stationLatitude': '37.636292',
      'stationLongitude': '127.023376',
      'stationName': '1535. 효성인텔리안 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1110',
      'stationLatitude': '37.636261',
      'stationLongitude': '127.032173',
      'stationName': '1536. 번동 두산위브 101동 옆'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1387',
      'stationLatitude': '37.663666',
      'stationLongitude': '127.012428',
      'stationName': '1537. 북한산 우이역'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '8',
      'shared': '150',
      'stationId': 'ST-1388',
      'stationLatitude': '37.656158',
      'stationLongitude': '127.013138',
      'stationName': '1538. 솔밭공원역'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1389',
      'stationLatitude': '37.649673',
      'stationLongitude': '127.013451',
      'stationName': '1539. 4.19민주묘지역'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '13',
      'shared': '123',
      'stationId': 'ST-211',
      'stationLatitude': '37.560909',
      'stationLongitude': '126.905495',
      'stationName': '154. 마포구청역 '},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1390',
      'stationLatitude': '37.641670',
      'stationLongitude': '127.016884',
      'stationName': '1540. 가오리역'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1391',
      'stationLatitude': '37.626530',
      'stationLongitude': '127.018059',
      'stationName': '1541. 삼양역'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1392',
      'stationLatitude': '37.621552',
      'stationLongitude': '127.020370',
      'stationName': '1542. 삼양사거리역'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1423',
      'stationLatitude': '37.630188',
      'stationLongitude': '127.017738',
      'stationName': '1543. 수유1동 주민센터'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1614',
      'stationLatitude': '37.620380',
      'stationLongitude': '127.013680',
      'stationName': '1545. 솔샘역 2번 출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1665',
      'stationLatitude': '37.615459',
      'stationLongitude': '127.029701',
      'stationName': '1546. 송천동우체국'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1724',
      'stationLatitude': '37.618641',
      'stationLongitude': '127.036240',
      'stationName': '1547. 꿈의숲 롯데캐슬'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1725',
      'stationLatitude': '37.622688',
      'stationLongitude': '127.037811',
      'stationName': '1548. 북서울 꿈의숲 서문'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-212',
      'stationLatitude': '37.568550',
      'stationLongitude': '126.914513',
      'stationName': '155. 가좌역1 번출구 뒤'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-213',
      'stationLatitude': '37.549904',
      'stationLongitude': '126.955147',
      'stationName': '156. 서울서부지방법원 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-214',
      'stationLatitude': '37.553001',
      'stationLongitude': '126.956688',
      'stationName': '157. 애오개역 4번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-215',
      'stationLatitude': '37.571259',
      'stationLongitude': '126.960480',
      'stationName': '158. 독립문 어린이 공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '7',
      'shared': '57',
      'stationId': 'ST-216',
      'stationLatitude': '37.556953',
      'stationLongitude': '126.946342',
      'stationName': '159. 이대역 4번 출구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-217',
      'stationLatitude': '37.557549',
      'stationLongitude': '126.959381',
      'stationName': '160. 북아현동 가구거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-218',
      'stationLatitude': '37.582245',
      'stationLongitude': '126.950645',
      'stationName': '161. 무악재역1번 출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-219',
      'stationLatitude': '37.565269',
      'stationLongitude': '126.946243',
      'stationName': '162. 봉원고가차도 밑'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '7',
      'shared': '14',
      'stationId': 'ST-220',
      'stationLatitude': '37.583698',
      'stationLongitude': '126.924965',
      'stationName': '163. 명지전문대학교 정문 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-221',
      'stationLatitude': '37.574478',
      'stationLongitude': '126.910049',
      'stationName': '164. 북가좌1동 주민센터 '},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1111',
      'stationLatitude': '37.617367',
      'stationLongitude': '127.075211',
      'stationName': '1643. 태릉입구역 8번출구'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-1114',
      'stationLatitude': '37.638489',
      'stationLongitude': '127.107903',
      'stationName': '1646. 삼육대 입구'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-222',
      'stationLatitude': '37.575138',
      'stationLongitude': '126.913940',
      'stationName': '165. 중앙근린공원'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '20',
      'shared': '75',
      'stationId': 'ST-1118',
      'stationLatitude': '37.639580',
      'stationLongitude': '127.065102',
      'stationName': '1650. 중계근린공원내'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '20',
      'shared': '25',
      'stationId': 'ST-1119',
      'stationLatitude': '37.672375',
      'stationLongitude': '127.055992',
      'stationName': '1651. 맥도날드 상계점 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1120',
      'stationLatitude': '37.680000',
      'stationLongitude': '127.055580',
      'stationName': '1652. 파르코 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1121',
      'stationLatitude': '37.656200',
      'stationLongitude': '127.063622',
      'stationName': '1653. 노원역1번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-1122',
      'stationLatitude': '37.663792',
      'stationLongitude': '127.075447',
      'stationName': '1654. 당고개입구 오거리'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1123',
      'stationLatitude': '37.631111',
      'stationLongitude': '127.070160',
      'stationName': '1655. 공릉1단지아파트'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1124',
      'stationLatitude': '37.654999',
      'stationLongitude': '127.067436',
      'stationName': '1656. 중앙하이츠 아파트 입구'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '10',
      'shared': '180',
      'stationId': 'ST-1125',
      'stationLatitude': '37.654049',
      'stationLongitude': '127.057327',
      'stationName': '1657. 노원구청 '},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1127',
      'stationLatitude': '37.650330',
      'stationLongitude': '127.071602',
      'stationName': '1659. 중계동 을지중학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-223',
      'stationLatitude': '37.573277',
      'stationLongitude': '126.919678',
      'stationName': '166. 가재울 초등학교'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1128',
      'stationLatitude': '37.642071',
      'stationLongitude': '127.076622',
      'stationName': '1660. 서울시립과학관'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1278',
      'stationLatitude': '37.649639',
      'stationLongitude': '127.065605',
      'stationName': '1661. 당현천근린공원'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1279',
      'stationLatitude': '37.654114',
      'stationLongitude': '127.059151',
      'stationName': '1662. 노원역7번출구'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '20',
      'shared': '90',
      'stationId': 'ST-1280',
      'stationLatitude': '37.619381',
      'stationLongitude': '127.057854',
      'stationName': '1663. 동해문화예술관앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1281',
      'stationLatitude': '37.649361',
      'stationLongitude': '127.070442',
      'stationName': '1664. 노해근린공원내'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1282',
      'stationLatitude': '37.647335',
      'stationLongitude': '127.076424',
      'stationName': '1665. 양지근린공원앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1283',
      'stationLatitude': '37.655781',
      'stationLongitude': '127.071777',
      'stationName': '1666. 노원소방서인근'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1284',
      'stationLatitude': '37.654499',
      'stationLongitude': '127.074387',
      'stationName': '1667. 중계중학교'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1285',
      'stationLatitude': '37.645508',
      'stationLongitude': '127.063255',
      'stationName': '1668. 중계역 6번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-1286',
      'stationLatitude': '37.643528',
      'stationLongitude': '127.065224',
      'stationName': '1669. 중계역 3번출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-224',
      'stationLatitude': '37.579460',
      'stationLongitude': '126.917130',
      'stationName': '167. 연가초등학교 옆'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1287',
      'stationLatitude': '37.643410',
      'stationLongitude': '127.071838',
      'stationName': '1670. 노원경찰서교차로'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '15',
      'shared': '153',
      'stationId': 'ST-1288',
      'stationLatitude': '37.629349',
      'stationLongitude': '127.054825',
      'stationName': '1671. 인덕대학교'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-1289',
      'stationLatitude': '37.688599',
      'stationLongitude': '127.053406',
      'stationName': '1672. 상계동수락리버시티'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1290',
      'stationLatitude': '37.653976',
      'stationLongitude': '127.060974',
      'stationName': '1673. 노원역\xa05번출구'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-1291',
      'stationLatitude': '37.653549',
      'stationLongitude': '127.058083',
      'stationName': '1674. 서울북부고용센터앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '14',
      'shared': '0',
      'stationId': 'ST-1348',
      'stationLatitude': '37.626942',
      'stationLongitude': '127.055130',
      'stationName': '1675. 월계문화체육센터'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1349',
      'stationLatitude': '37.623165',
      'stationLongitude': '127.090500',
      'stationName': '1677. 육군사관학교  앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-1394',
      'stationLatitude': '37.648438',
      'stationLongitude': '127.064445',
      'stationName': '1678. 성서대학교 밀알관'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1395',
      'stationLatitude': '37.642830',
      'stationLongitude': '127.106667',
      'stationName': '1679. 삼육대 도서관'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1396',
      'stationLatitude': '37.642654',
      'stationLongitude': '127.108383',
      'stationName': '1680. 삼육대 제3과학관'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '12',
      'shared': '17',
      'stationId': 'ST-1425',
      'stationLatitude': '37.645802',
      'stationLongitude': '127.082260',
      'stationName': '1681. 현대6차 아파트'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '13',
      'shared': '23',
      'stationId': 'ST-1426',
      'stationLatitude': '37.656799',
      'stationLongitude': '127.077606',
      'stationName': '1682. 중계종합사회복지관 교차로'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1473',
      'stationLatitude': '37.650459',
      'stationLongitude': '127.080887',
      'stationName': '1683. 노원문화예술회관'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1474',
      'stationLatitude': '37.618320',
      'stationLongitude': '127.075630',
      'stationName': '1684. 태릉입구역 5번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1475',
      'stationLatitude': '37.648190',
      'stationLongitude': '127.080482',
      'stationName': '1685. 불암고등학교 앞 횡단보도'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1476',
      'stationLatitude': '37.661140',
      'stationLongitude': '127.058052',
      'stationName': '1686. 온수골사거리(스타벅스앞)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1477',
      'stationLatitude': '0.000000',
      'stationLongitude': '0.000000',
      'stationName': '1687. 서울월드컵경기장 테스트'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '9',
      'shared': '44',
      'stationId': 'ST-1639',
      'stationLatitude': '37.665661',
      'stationLongitude': '127.057297',
      'stationName': '1688. 마들역 7번출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1640',
      'stationLatitude': '37.665249',
      'stationLongitude': '127.057892',
      'stationName': '1689. 마들역 3번출구'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '15',
      'shared': '80',
      'stationId': 'ST-226',
      'stationLatitude': '37.573002',
      'stationLongitude': '126.907799',
      'stationName': '169. 북가좌 삼거리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1641',
      'stationLatitude': '37.657730',
      'stationLongitude': '127.059311',
      'stationName': '1690. 도봉운전면허시험장'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1642',
      'stationLatitude': '37.660709',
      'stationLongitude': '127.065331',
      'stationName': '1691. 노원정보도서관'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1672',
      'stationLatitude': '37.664188',
      'stationLongitude': '127.066010',
      'stationName': '1692. 온곡초교 교차로'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-1740',
      'stationLatitude': '37.628189',
      'stationLongitude': '127.082108',
      'stationName': '1693. 원자력 병원'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-227',
      'stationLatitude': '37.573112',
      'stationLongitude': '126.922447',
      'stationName': '170. 가재울 뉴타운 주유소 옆'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-228',
      'stationLatitude': '37.564724',
      'stationLongitude': '126.967278',
      'stationName': '171. 임광빌딩 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1129',
      'stationLatitude': '37.647266',
      'stationLongitude': '127.025879',
      'stationName': '1713. 쌍문동 청소년 랜드'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1130',
      'stationLatitude': '37.644630',
      'stationLongitude': '127.044609',
      'stationName': '1714. 도봉문화정보도서관 삼거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1131',
      'stationLatitude': '37.653179',
      'stationLongitude': '127.012787',
      'stationName': '1715. 서울특별시교육청도봉도서관'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1132',
      'stationLatitude': '37.654202',
      'stationLongitude': '127.050728',
      'stationName': '1716. 하나로마트 창동점'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1133',
      'stationLatitude': '37.655708',
      'stationLongitude': '127.050102',
      'stationName': '1717. 시립창동운동장 입구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1135',
      'stationLatitude': '37.673283',
      'stationLongitude': '127.043991',
      'stationName': '1719. 신도봉사거리 버스정류장'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '27',
      'shared': '37',
      'stationId': 'ST-1136',
      'stationLatitude': '37.668671',
      'stationLongitude': '127.047981',
      'stationName': '1720. 도봉구청 옆(중랑천변)'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '12',
      'shared': '142',
      'stationId': 'ST-1137',
      'stationLatitude': '37.653015',
      'stationLongitude': '127.046997',
      'stationName': '1721. 창동역 2번출구 '},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1292',
      'stationLatitude': '37.657799',
      'stationLongitude': '127.050049',
      'stationName': '1722. 창동청소년수련관'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1293',
      'stationLatitude': '37.662079',
      'stationLongitude': '127.027718',
      'stationName': '1723. 방학동학마을도서관'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1295',
      'stationLatitude': '37.647503',
      'stationLongitude': '127.043312',
      'stationName': '1725. 창1동주민센터'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '8',
      'shared': '38',
      'stationId': 'ST-1296',
      'stationLatitude': '37.658588',
      'stationLongitude': '127.035210',
      'stationName': '1726. 삼익세라믹아파트교차로'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '15',
      'shared': '133',
      'stationId': 'ST-1297',
      'stationLatitude': '37.678677',
      'stationLongitude': '127.040764',
      'stationName': '1727. 서울도봉초등학교인근'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '15',
      'shared': '120',
      'stationId': 'ST-1434',
      'stationLatitude': '37.677666',
      'stationLongitude': '127.046242',
      'stationName': '1728. 서울북부지방법원'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1461',
      'stationLatitude': '37.684010',
      'stationLongitude': '127.045792',
      'stationName': '1729. 파리바게트앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-230',
      'stationLatitude': '37.564777',
      'stationLongitude': '126.966148',
      'stationName': '173. 서대문역 8번출구 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1462',
      'stationLatitude': '37.687592',
      'stationLongitude': '127.045502',
      'stationName': '1730. 도봉산역 교차로 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-1463',
      'stationLatitude': '37.687500',
      'stationLongitude': '127.042557',
      'stationName': '1731. 도봉고등학교 맞은편'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1464',
      'stationLatitude': '37.667599',
      'stationLongitude': '127.042999',
      'stationName': '1732. 우리은행 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '12',
      'shared': '133',
      'stationId': 'ST-1465',
      'stationLatitude': '37.662979',
      'stationLongitude': '127.041939',
      'stationName': '1733. 방학사거리 (봄마당 앞)'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1466',
      'stationLatitude': '37.658150',
      'stationLongitude': '127.032669',
      'stationName': '1734. 쌍문현대1차아파트 108동 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '13',
      'shared': '69',
      'stationId': 'ST-1467',
      'stationLatitude': '37.679119',
      'stationLongitude': '127.044983',
      'stationName': '1735. 도봉역 1,2번 출구사이 건너편'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '12',
      'shared': '50',
      'stationId': 'ST-1468',
      'stationLatitude': '37.652241',
      'stationLongitude': '127.037064',
      'stationName': '1736. 버스정류장 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '8',
      'shared': '88',
      'stationId': 'ST-1469',
      'stationLatitude': '37.639702',
      'stationLongitude': '127.038834',
      'stationName': '1737. 하나은행 (창동점)'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1470',
      'stationLatitude': '37.646309',
      'stationLongitude': '127.052742',
      'stationName': '1738. 창동주공17단지 상가앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1638',
      'stationLatitude': '37.645199',
      'stationLongitude': '127.032982',
      'stationName': '1741. 제일강산수산입구'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1726',
      'stationLatitude': '37.648891',
      'stationLongitude': '127.023018',
      'stationName': '1742. 북한산 코오롱 하늘채'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '20',
      'shared': '40',
      'stationId': 'ST-231',
      'stationLatitude': '37.578072',
      'stationLongitude': '126.930817',
      'stationName': '175. 홍연2교옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-345',
      'stationLatitude': '37.577675',
      'stationLongitude': '126.909805',
      'stationName': '177. 북가좌 초등학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-349',
      'stationLatitude': '37.579876',
      'stationLongitude': '126.906349',
      'stationName': '178. 증산3교 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '15',
      'shared': '100',
      'stationId': 'ST-232',
      'stationLatitude': '37.569122',
      'stationLongitude': '126.914795',
      'stationName': '179. 가좌역 4번출구 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-233',
      'stationLatitude': '37.559967',
      'stationLongitude': '126.962463',
      'stationName': '180. 충정로역 7번출구 아래'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-339',
      'stationLatitude': '37.551342',
      'stationLongitude': '126.902672',
      'stationName': '181. 망원초록길 입구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-340',
      'stationLatitude': '37.551567',
      'stationLongitude': '126.902847',
      'stationName': '182. 망원2빗물펌프장 앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-341',
      'stationLatitude': '37.565166',
      'stationLongitude': '126.919395',
      'stationName': '183. 하늘채코오롱아파트 건너편'},
     {'parkingBikeTotCnt': '38',
      'rackTotCnt': '20',
      'shared': '190',
      'stationId': 'ST-1140',
      'stationLatitude': '37.477058',
      'stationLongitude': '126.885185',
      'stationName': '1839. 수출의 다리 아래'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-342',
      'stationLatitude': '37.558949',
      'stationLongitude': '126.907753',
      'stationName': '184. SK망원동주유소 건너편'},
     {'parkingBikeTotCnt': '35',
      'rackTotCnt': '20',
      'shared': '175',
      'stationId': 'ST-1141',
      'stationLatitude': '37.475101',
      'stationLongitude': '126.888069',
      'stationName': '1840. 솔브레인이엔지 뒤편'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1142',
      'stationLatitude': '37.476952',
      'stationLongitude': '126.891869',
      'stationName': '1841. 가산동 주민센터'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1143',
      'stationLatitude': '37.462574',
      'stationLongitude': '126.906860',
      'stationName': '1842. 한울중학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1144',
      'stationLatitude': '37.477097',
      'stationLongitude': '126.911133',
      'stationName': '1843. 독산고등학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1146',
      'stationLatitude': '37.460289',
      'stationLongitude': '126.892189',
      'stationName': '1845. 롯데캐슬골드파크1차 서문'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1147',
      'stationLatitude': '37.460171',
      'stationLongitude': '126.896042',
      'stationName': '1846. 롯데캐슬골드파크1차 동문'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1148',
      'stationLatitude': '37.461033',
      'stationLongitude': '126.887100',
      'stationName': '1847. 독산주공 14단지 버스정류소'},
     {'parkingBikeTotCnt': '39',
      'rackTotCnt': '10',
      'shared': '390',
      'stationId': 'ST-1149',
      'stationLatitude': '37.476276',
      'stationLongitude': '126.885391',
      'stationName': '1848. 벽산 디지털밸리 5차'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1276',
      'stationLatitude': '37.481354',
      'stationLongitude': '126.886940',
      'stationName': '1849. 대륭포스트타워5차'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-343',
      'stationLatitude': '37.542545',
      'stationLongitude': '126.934296',
      'stationName': '185. 마포 신수공원 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1277',
      'stationLatitude': '37.480160',
      'stationLongitude': '126.886368',
      'stationName': '1850. 코오롱테크노밸리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1403',
      'stationLatitude': '37.481232',
      'stationLongitude': '126.881485',
      'stationName': '1851. 가산디지털단지 7번출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1533',
      'stationLatitude': '37.451771',
      'stationLongitude': '126.913399',
      'stationName': '1852. 혜명양로원 담장 옆'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1534',
      'stationLatitude': '37.472481',
      'stationLongitude': '126.895866',
      'stationName': '1853. 서울디자인직업전문학교 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1535',
      'stationLatitude': '37.478180',
      'stationLongitude': '126.897408',
      'stationName': '1854. 가산아네스트 오피스텔 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1536',
      'stationLatitude': '37.451321',
      'stationLongitude': '126.897621',
      'stationName': '1855. 성지아파트 옆 도로변'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1537',
      'stationLatitude': '37.478409',
      'stationLongitude': '126.907372',
      'stationName': '1856. 모두의학교'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-1538',
      'stationLatitude': '37.460560',
      'stationLongitude': '126.887093',
      'stationName': '1857. 주공14단지'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1648',
      'stationLatitude': '37.437271',
      'stationLongitude': '126.902687',
      'stationName': '1858. 석수역1번출구 앞 (SK주유소)'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '20',
      'shared': '80',
      'stationId': 'ST-1734',
      'stationLatitude': '37.467999',
      'stationLongitude': '126.886841',
      'stationName': '1859. 대륭테크노타운 18차'},
     {'parkingBikeTotCnt': '33',
      'rackTotCnt': '40',
      'shared': '83',
      'stationId': 'ST-344',
      'stationLatitude': '37.563965',
      'stationLongitude': '126.898209',
      'stationName': '186. 월드컵공원'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-346',
      'stationLatitude': '37.586388',
      'stationLongitude': '126.935127',
      'stationName': '188. 홍은동 정원여중 입구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-347',
      'stationLatitude': '37.578892',
      'stationLongitude': '126.910736',
      'stationName': '191. 정명학원'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-348',
      'stationLatitude': '37.572227',
      'stationLongitude': '126.923065',
      'stationName': '192. 연서어린이공원'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-350',
      'stationLatitude': '37.577316',
      'stationLongitude': '126.902969',
      'stationName': '194. 증산교 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-351',
      'stationLatitude': '37.567657',
      'stationLongitude': '126.917809',
      'stationName': '195. 모래내고가차도 '},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1218',
      'stationLatitude': '37.510010',
      'stationLongitude': '126.882050',
      'stationName': '1956. 도야미리숯불갈비 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1219',
      'stationLatitude': '37.493401',
      'stationLongitude': '126.874329',
      'stationName': '1957. 구일고등학교 정문 '},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1220',
      'stationLatitude': '37.495781',
      'stationLongitude': '126.890121',
      'stationName': '1958. 강서수도사업소민원센터'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1221',
      'stationLatitude': '37.496456',
      'stationLongitude': '126.889587',
      'stationName': '1959. 구로구의회 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-352',
      'stationLatitude': '37.566120',
      'stationLongitude': '126.925896',
      'stationName': '196. 연희교차로 인근'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1222',
      'stationLatitude': '37.502850',
      'stationLongitude': '126.889481',
      'stationName': '1960. 화광신문사 앞'},
     {'parkingBikeTotCnt': '32',
      'rackTotCnt': '15',
      'shared': '213',
      'stationId': 'ST-1223',
      'stationLatitude': '37.508194',
      'stationLongitude': '126.891304',
      'stationName': '1961. 신도림테크노근린공원'},
     {'parkingBikeTotCnt': '31',
      'rackTotCnt': '15',
      'shared': '207',
      'stationId': 'ST-1224',
      'stationLatitude': '37.481602',
      'stationLongitude': '126.892799',
      'stationName': '1962. 가리봉동주민센터'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1226',
      'stationLatitude': '37.497890',
      'stationLongitude': '126.864502',
      'stationName': '1964. 원메디타운 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '15',
      'shared': '47',
      'stationId': 'ST-1227',
      'stationLatitude': '37.497231',
      'stationLongitude': '126.859192',
      'stationName': '1965. 삼환로즈빌아파트 105동 옆'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1228',
      'stationLatitude': '37.496498',
      'stationLongitude': '126.863098',
      'stationName': '1966. 한마을아파트 정문상가'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1229',
      'stationLatitude': '37.505138',
      'stationLongitude': '126.844337',
      'stationName': '1967. 참새공원(백곡경노당)'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '12',
      'shared': '100',
      'stationId': 'ST-1230',
      'stationLatitude': '37.498482',
      'stationLongitude': '126.847504',
      'stationName': '1968. 동인오피스텔 건너편 소공원'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1231',
      'stationLatitude': '37.501904',
      'stationLongitude': '126.828964',
      'stationName': '1969. 궁동생태공원'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1233',
      'stationLatitude': '37.490723',
      'stationLongitude': '126.826393',
      'stationName': '1971. 오정초교 앞 보도육교'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1235',
      'stationLatitude': '37.488598',
      'stationLongitude': '126.836494',
      'stationName': '1973. 오리로와 서해안도로 교차로 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1237',
      'stationLatitude': '37.492565',
      'stationLongitude': '126.894753',
      'stationName': '1975. 대림역 1번 출입구 밑'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1238',
      'stationLatitude': '37.485680',
      'stationLongitude': '126.886703',
      'stationName': '1976. 남구로역 5번 출입구 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1241',
      'stationLatitude': '37.492031',
      'stationLongitude': '126.873772',
      'stationName': '1979. 구로1동우체국 앞'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '15',
      'shared': '140',
      'stationId': 'ST-354',
      'stationLatitude': '37.562138',
      'stationLongitude': '126.963776',
      'stationName': '198. 충정2교'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1243',
      'stationLatitude': '37.479431',
      'stationLongitude': '126.842697',
      'stationName': '1981. 천왕이펜하우스5단지 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1273',
      'stationLatitude': '37.502548',
      'stationLongitude': '126.883881',
      'stationName': '1983. 구로동롯데아파트'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '10',
      'shared': '190',
      'stationId': 'ST-1274',
      'stationLatitude': '37.495266',
      'stationLongitude': '126.888474',
      'stationName': '1984. 구로구청'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-1275',
      'stationLatitude': '37.498516',
      'stationLongitude': '126.891991',
      'stationName': '1985. 구로도서관'},
     {'parkingBikeTotCnt': '71',
      'rackTotCnt': '15',
      'shared': '473',
      'stationId': 'ST-1521',
      'stationLatitude': '37.484859',
      'stationLongitude': '126.895187',
      'stationName': '1986. 태평양물산빌딩'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1522',
      'stationLatitude': '37.490341',
      'stationLongitude': '126.860931',
      'stationName': '1987. 개봉아이파크아파트 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1523',
      'stationLatitude': '37.506050',
      'stationLongitude': '126.860786',
      'stationName': '1988. 고척LIGA아파트 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '30',
      'shared': '47',
      'stationId': 'ST-443',
      'stationLatitude': '37.566845',
      'stationLongitude': '126.896446',
      'stationName': '199. 서울 월드컵 경기장'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1526',
      'stationLatitude': '37.496761',
      'stationLongitude': '126.844963',
      'stationName': '1991. 오류동역 맞은편'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '19',
      'shared': '84',
      'stationId': 'ST-1527',
      'stationLatitude': '37.491798',
      'stationLongitude': '126.832420',
      'stationName': '1992. 구로구배드민턴실내체육관 앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1528',
      'stationLatitude': '37.489380',
      'stationLongitude': '126.834198',
      'stationName': '1993. 금강수목원아파트 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1529',
      'stationLatitude': '37.496998',
      'stationLongitude': '126.871780',
      'stationName': '1994. 삼성전자 물류센터 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1531',
      'stationLatitude': '37.495399',
      'stationLongitude': '126.871010',
      'stationName': '1996. 구일역 1번 출입구 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '8',
      'shared': '188',
      'stationId': 'ST-1696',
      'stationLatitude': '37.498569',
      'stationLongitude': '126.871521',
      'stationName': '1998. 고척교 교차로'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '15',
      'shared': '140',
      'stationId': 'ST-1732',
      'stationLatitude': '37.495258',
      'stationLongitude': '126.830658',
      'stationName': '1999. 수궁동 성당 주변'},
     {'parkingBikeTotCnt': '36',
      'rackTotCnt': '20',
      'shared': '180',
      'stationId': 'ST-45',
      'stationLatitude': '37.528416',
      'stationLongitude': '126.913918',
      'stationName': '200. 국회의원회관'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-1733',
      'stationLatitude': '37.512329',
      'stationLongitude': '126.886833',
      'stationName': '2000. 신도림4차 e편한세상 아파트 1109동 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1150',
      'stationLatitude': '37.513523',
      'stationLongitude': '126.943527',
      'stationName': '2058. 노량진동 맥도널드앞'},
     {'parkingBikeTotCnt': '33',
      'rackTotCnt': '10',
      'shared': '330',
      'stationId': 'ST-1151',
      'stationLatitude': '37.497078',
      'stationLongitude': '126.917793',
      'stationName': '2059. 보라매공원 정문'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1152',
      'stationLatitude': '37.484631',
      'stationLongitude': '126.971550',
      'stationName': '2060. 남성역3번출구 뒤'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1153',
      'stationLatitude': '37.505928',
      'stationLongitude': '126.969231',
      'stationName': '2061. 한강 현대아파트 건너편'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1154',
      'stationLatitude': '37.486652',
      'stationLongitude': '126.967842',
      'stationName': '2062. 사당새마을금고'},
     {'parkingBikeTotCnt': '30',
      'rackTotCnt': '15',
      'shared': '200',
      'stationId': 'ST-1354',
      'stationLatitude': '37.512901',
      'stationLongitude': '126.926613',
      'stationName': '2063. 대방역 4번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1355',
      'stationLatitude': '37.505356',
      'stationLongitude': '126.966179',
      'stationName': '2064. 흑석한강푸르지오 106동앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1356',
      'stationLatitude': '37.511990',
      'stationLongitude': '126.927086',
      'stationName': '2065. 서울시여성가족재단'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1542',
      'stationLatitude': '37.489399',
      'stationLongitude': '126.907112',
      'stationName': '2066. 양문교회 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1543',
      'stationLatitude': '37.497669',
      'stationLongitude': '126.919868',
      'stationName': '2067. LG전자 베스트샾 대리점 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-1544',
      'stationLatitude': '37.488159',
      'stationLongitude': '126.966476',
      'stationName': '2068. 총신대 앞(육교)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '7',
      'shared': '29',
      'stationId': 'ST-1667',
      'stationLatitude': '37.496601',
      'stationLongitude': '126.953682',
      'stationName': '2069. 숭실대 입구역3번 출구 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '12',
      'shared': '92',
      'stationId': 'ST-1545',
      'stationLatitude': '37.513920',
      'stationLongitude': '126.943069',
      'stationName': '2070. 노량진역 2번 출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1742',
      'stationLatitude': '37.488869',
      'stationLongitude': '126.971909',
      'stationName': '2071. 대림아파트 후문 상가 옆'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1156',
      'stationLatitude': '37.475090',
      'stationLongitude': '126.959229',
      'stationName': '2159. 인헌초교'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1157',
      'stationLatitude': '37.478626',
      'stationLongitude': '126.951294',
      'stationName': '2160. 관악구 보건소'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1259',
      'stationLatitude': '37.484768',
      'stationLongitude': '126.932877',
      'stationName': '2164. 관악우체국'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1260',
      'stationLatitude': '37.476482',
      'stationLongitude': '126.965363',
      'stationName': '2165. JK장평타워'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '12',
      'shared': '42',
      'stationId': 'ST-1262',
      'stationLatitude': '37.476295',
      'stationLongitude': '126.964958',
      'stationName': '2167. 낙성대역 1번출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '7',
      'shared': '114',
      'stationId': 'ST-1264',
      'stationLatitude': '37.482189',
      'stationLongitude': '126.942131',
      'stationName': '2169. 봉천역 2번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1265',
      'stationLatitude': '37.481529',
      'stationLongitude': '126.912033',
      'stationName': '2170. 조원동서울본병원'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '17',
      'shared': '18',
      'stationId': 'ST-1337',
      'stationLatitude': '37.481548',
      'stationLongitude': '126.952003',
      'stationName': '2171. 서울대입구역 5번출구'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '20',
      'shared': '65',
      'stationId': 'ST-1267',
      'stationLatitude': '37.469406',
      'stationLongitude': '126.944511',
      'stationName': '2172. 나들목공원'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1268',
      'stationLatitude': '37.489750',
      'stationLongitude': '126.927467',
      'stationName': '2173. 당곡사거리'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1269',
      'stationLatitude': '37.488564',
      'stationLongitude': '126.928482',
      'stationName': '2174. 삼성디지털프라자관악점'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1270',
      'stationLatitude': '37.487301',
      'stationLongitude': '126.928703',
      'stationName': '2175. 신림동걷고싶은문화의거리입구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1357',
      'stationLatitude': '37.488991',
      'stationLongitude': '126.916382',
      'stationName': '2176. 보라매공원 보도육교'},
     {'parkingBikeTotCnt': '25',
      'rackTotCnt': '19',
      'shared': '132',
      'stationId': 'ST-1546',
      'stationLatitude': '37.487129',
      'stationLongitude': '126.913017',
      'stationName': '2177. 신대방역 2번 출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1547',
      'stationLatitude': '37.466820',
      'stationLongitude': '126.948807',
      'stationName': '2178. 서울대학교 정문'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1548',
      'stationLatitude': '37.482189',
      'stationLongitude': '126.946159',
      'stationName': '2179. 양녕로 입구'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1549',
      'stationLatitude': '37.487511',
      'stationLongitude': '126.927788',
      'stationName': '2180. 신림동주민센터'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-1678',
      'stationLatitude': '37.471828',
      'stationLongitude': '126.933922',
      'stationName': '2183. 동방1교'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1702',
      'stationLatitude': '37.489491',
      'stationLongitude': '126.945923',
      'stationName': '2184. 구암초등학교 버스정류장'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-1158',
      'stationLatitude': '37.490540',
      'stationLongitude': '127.008163',
      'stationName': '2266. 서초역 3번출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1160',
      'stationLatitude': '37.502319',
      'stationLongitude': '127.022270',
      'stationName': '2268. 서초4동주민센터 '},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1161',
      'stationLatitude': '37.510349',
      'stationLongitude': '127.016052',
      'stationName': '2269. 주홍교 하부'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-277',
      'stationLatitude': '37.544666',
      'stationLongitude': '126.888359',
      'stationName': '227. 양평2나들목 보행통로 입구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1162',
      'stationLatitude': '37.448967',
      'stationLongitude': '127.057739',
      'stationName': '2270. 서초포레스타 7단지'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1163',
      'stationLatitude': '37.487865',
      'stationLongitude': '126.994293',
      'stationName': '2271. 내방역 8번출구 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1164',
      'stationLatitude': '37.487309',
      'stationLongitude': '127.010582',
      'stationName': '2272. 교대입구 교차로'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1165',
      'stationLatitude': '37.477829',
      'stationLongitude': '127.038269',
      'stationName': '2273. 일동제약 사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1166',
      'stationLatitude': '37.469650',
      'stationLongitude': '127.039612',
      'stationName': '2274. 양재시민의숲역 3번출구'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1167',
      'stationLatitude': '37.461578',
      'stationLongitude': '127.048798',
      'stationName': '2275. 염곡치안센터 건너편'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1168',
      'stationLatitude': '37.474388',
      'stationLongitude': '127.038902',
      'stationName': '2276. 영동1교 (양재천근린공원)'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1169',
      'stationLatitude': '37.514870',
      'stationLongitude': '127.015282',
      'stationName': '2277. 길마중4교 하부'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1305',
      'stationLatitude': '37.493618',
      'stationLongitude': '127.014183',
      'stationName': '2279. 교대역 5번출구뒤'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-278',
      'stationLatitude': '37.538460',
      'stationLongitude': '126.894508',
      'stationName': '228. 선유도역 3번출구 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1306',
      'stationLatitude': '37.484161',
      'stationLongitude': '127.010971',
      'stationName': '2280. 서울서초고용센터앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '7',
      'shared': '0',
      'stationId': 'ST-1307',
      'stationLatitude': '37.475979',
      'stationLongitude': '126.986282',
      'stationName': '2281. 연세사랑병원신관앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '15',
      'shared': '100',
      'stationId': 'ST-1308',
      'stationLatitude': '37.477203',
      'stationLongitude': '127.005836',
      'stationName': '2282. 방배래미안아트힐 101동앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1309',
      'stationLatitude': '37.486526',
      'stationLongitude': '126.989166',
      'stationName': '2283. 그룹한빌딩옆'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1310',
      'stationLatitude': '37.468102',
      'stationLongitude': '126.986801',
      'stationName': '2284. CJ오쇼핑앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-1311',
      'stationLatitude': '37.457424',
      'stationLongitude': '127.022652',
      'stationName': '2285. LH서초3단지 301동 맞은편'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1312',
      'stationLatitude': '37.458549',
      'stationLongitude': '127.055885',
      'stationName': '2286. 탑성마을입구'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1313',
      'stationLatitude': '37.455620',
      'stationLongitude': '127.067101',
      'stationName': '2287. 능안마을입구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1314',
      'stationLatitude': '37.455608',
      'stationLongitude': '127.064453',
      'stationName': '2288. 안골마을입구'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1315',
      'stationLatitude': '37.464298',
      'stationLongitude': '126.988525',
      'stationName': '2289. 남태령역 2번출구'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '20',
      'shared': '115',
      'stationId': 'ST-279',
      'stationLatitude': '37.535873',
      'stationLongitude': '126.892181',
      'stationName': '229. 양평1 보행육교 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1316',
      'stationLatitude': '37.499413',
      'stationLongitude': '126.999413',
      'stationName': '2290. 서래마을파리15구공원앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-1359',
      'stationLatitude': '37.488243',
      'stationLongitude': '127.027016',
      'stationName': '2292. 무지개아파트 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1360',
      'stationLatitude': '37.484798',
      'stationLongitude': '127.036995',
      'stationName': '2293. SPC 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '15',
      'shared': '100',
      'stationId': 'ST-1361',
      'stationLatitude': '37.475906',
      'stationLongitude': '127.046242',
      'stationName': '2294. 두상빌딩 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1404',
      'stationLatitude': '37.485672',
      'stationLongitude': '127.015923',
      'stationName': '2297. 남부터미널역 1번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '12',
      'shared': '17',
      'stationId': 'ST-1405',
      'stationLatitude': '37.502411',
      'stationLongitude': '127.021606',
      'stationName': '2298. 래미안서초스위트앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-1406',
      'stationLatitude': '37.486469',
      'stationLongitude': '127.028061',
      'stationName': '2299. 한전아트센터 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-413',
      'stationLatitude': '37.524635',
      'stationLongitude': '126.896217',
      'stationName': '230. 영등포구청역 1번출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-280',
      'stationLatitude': '37.524506',
      'stationLongitude': '126.891823',
      'stationName': '231. 남부고용노동지청 남측'},
     {'parkingBikeTotCnt': '50',
      'rackTotCnt': '20',
      'shared': '250',
      'stationId': 'ST-281',
      'stationLatitude': '37.525650',
      'stationLongitude': '126.887817',
      'stationName': '232. 양평우림 이비즈센타 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-282',
      'stationLatitude': '37.528488',
      'stationLongitude': '126.891647',
      'stationName': '233. YP 센터 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-283',
      'stationLatitude': '37.500462',
      'stationLongitude': '126.905846',
      'stationName': '234. 영등포구민체육센터 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-284',
      'stationLatitude': '37.504566',
      'stationLongitude': '126.910233',
      'stationName': '235. 신길동 우리은행 옆'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-285',
      'stationLatitude': '37.516155',
      'stationLongitude': '126.894615',
      'stationName': '236. 문래동자이아파트 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1170',
      'stationLatitude': '37.526844',
      'stationLongitude': '127.028259',
      'stationName': '2361. 압구정역 교차로'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1171',
      'stationLatitude': '37.517635',
      'stationLongitude': '127.022453',
      'stationName': '2362. 신사동 가로수길 입구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1172',
      'stationLatitude': '37.519180',
      'stationLongitude': '127.027466',
      'stationName': '2363. 강남 을지병원 교차로'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1173',
      'stationLatitude': '37.521240',
      'stationLongitude': '127.031898',
      'stationName': '2364. 도산대로 렉서스 앞'},
     {'parkingBikeTotCnt': '22',
      'rackTotCnt': '15',
      'shared': '147',
      'stationId': 'ST-1174',
      'stationLatitude': '37.523300',
      'stationLongitude': '127.038475',
      'stationName': '2365. K+ 타워 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1177',
      'stationLatitude': '37.489342',
      'stationLongitude': '127.041298',
      'stationName': '2368. 도곡동 경남아파트 건너편'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '20',
      'shared': '20',
      'stationId': 'ST-1178',
      'stationLatitude': '37.505428',
      'stationLongitude': '127.052872',
      'stationName': '2369. KT선릉타워'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '20',
      'shared': '70',
      'stationId': 'ST-286',
      'stationLatitude': '37.496513',
      'stationLongitude': '126.914803',
      'stationName': '237. 보라매 두산위브 건너편'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1179',
      'stationLatitude': '37.496552',
      'stationLongitude': '127.054298',
      'stationName': '2370. 한티역 3번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1180',
      'stationLatitude': '37.514748',
      'stationLongitude': '127.035133',
      'stationName': '2371. 한국우편사업진흥원'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1181',
      'stationLatitude': '37.494499',
      'stationLongitude': '127.063797',
      'stationName': '2372. 대치역 사거리'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '20',
      'shared': '75',
      'stationId': 'ST-1182',
      'stationLatitude': '37.489277',
      'stationLongitude': '127.065575',
      'stationName': '2373. 개포동역 사거리'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1184',
      'stationLatitude': '37.487350',
      'stationLongitude': '127.100998',
      'stationName': '2375. 수서역 1번출구 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '20',
      'shared': '10',
      'stationId': 'ST-1185',
      'stationLatitude': '37.486778',
      'stationLongitude': '127.100517',
      'stationName': '2376. 수서역 6번출구 앞'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '10',
      'shared': '190',
      'stationId': 'ST-1186',
      'stationLatitude': '37.486835',
      'stationLongitude': '127.102753',
      'stationName': '2377. 수서역 5번출구 뒤'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-287',
      'stationLatitude': '37.526386',
      'stationLongitude': '126.902756',
      'stationName': '238. 제2구민체육센타 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1245',
      'stationLatitude': '37.511696',
      'stationLongitude': '127.049347',
      'stationName': '2380. 삼성동베이직하우스앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1246',
      'stationLatitude': '37.506367',
      'stationLongitude': '127.034523',
      'stationName': '2381. 언주역 6번출구앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '11',
      'shared': '18',
      'stationId': 'ST-1247',
      'stationLatitude': '37.501343',
      'stationLongitude': '127.050468',
      'stationName': '2382. 역삼동 sk뷰 501동앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1248',
      'stationLatitude': '37.466328',
      'stationLongitude': '127.094887',
      'stationName': '2383. 보금자리정원'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1364',
      'stationLatitude': '37.476028',
      'stationLongitude': '127.105942',
      'stationName': '2384. 자곡사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1365',
      'stationLatitude': '37.513950',
      'stationLongitude': '127.030151',
      'stationName': '2385. 학동역'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1407',
      'stationLatitude': '37.472454',
      'stationLongitude': '127.096077',
      'stationName': '2387. 래미안강남힐즈 사거리'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1433',
      'stationLatitude': '37.516785',
      'stationLongitude': '127.051613',
      'stationName': '2388. 강남구 도시관리공단'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1559',
      'stationLatitude': '37.486160',
      'stationLongitude': '127.067238',
      'stationName': '2389. 경기여자고등학교 후문 (삼성로3길 입구)'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '20',
      'shared': '65',
      'stationId': 'ST-288',
      'stationLatitude': '37.525852',
      'stationLongitude': '126.903282',
      'stationName': '239. 유스호스텔 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1560',
      'stationLatitude': '37.480881',
      'stationLongitude': '127.063042',
      'stationName': '2390. 구룡마을 입구 (래미안블레스티지 아파트)'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1561',
      'stationLatitude': '37.475986',
      'stationLongitude': '127.059624',
      'stationName': '2391. 구룡마을 입구(개포1단지아파트)'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-1562',
      'stationLatitude': '37.474579',
      'stationLongitude': '127.055450',
      'stationName': '2392. 구룡산 입구 (구룡산 서울둘레길 입구)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1563',
      'stationLatitude': '37.472000',
      'stationLongitude': '127.051338',
      'stationName': '2393. 구룡사 앞 교차로 (보도육교)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1565',
      'stationLatitude': '37.479290',
      'stationLongitude': '127.055733',
      'stationName': '2395. 개포1단지아파트 입구 (보도육교)'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '15',
      'shared': '140',
      'stationId': 'ST-1566',
      'stationLatitude': '37.485741',
      'stationLongitude': '127.051048',
      'stationName': '2396. 영동3교 북단(우성캐릭터 앞 보도)'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1568',
      'stationLatitude': '37.508110',
      'stationLongitude': '127.039452',
      'stationName': '2398. 더라움'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '10',
      'shared': '180',
      'stationId': 'ST-289',
      'stationLatitude': '37.518738',
      'stationLongitude': '126.895576',
      'stationName': '240. 문래역 4번출구 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '15',
      'shared': '20',
      'stationId': 'ST-1571',
      'stationLatitude': '37.486561',
      'stationLongitude': '127.082672',
      'stationName': '2401. 밀알학교 입구 (삼성서울병원 입구)'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1573',
      'stationLatitude': '37.488720',
      'stationLongitude': '127.074539',
      'stationName': '2403. 공무원연금매점 교차로 (개포주공9단지 입구)'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1574',
      'stationLatitude': '37.491810',
      'stationLongitude': '127.073158',
      'stationName': '2404. 대모산입구역 4번 출구 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '20',
      'shared': '10',
      'stationId': 'ST-1575',
      'stationLatitude': '37.518711',
      'stationLongitude': '127.050850',
      'stationName': '2405. 청담공원앞 교차로'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1576',
      'stationLatitude': '37.517570',
      'stationLongitude': '127.023643',
      'stationName': '2406. 논현동 광명빌딩 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1577',
      'stationLatitude': '37.498470',
      'stationLongitude': '127.030113',
      'stationName': '2407. 역삼.서초.삼성 세무서 앞 (역삼빌딩 앞)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '14',
      'shared': '0',
      'stationId': 'ST-1578',
      'stationLatitude': '37.477341',
      'stationLongitude': '127.113274',
      'stationName': '2408. 강남한양수자인아파트'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '18',
      'shared': '33',
      'stationId': 'ST-1679',
      'stationLatitude': '37.492062',
      'stationLongitude': '127.030746',
      'stationName': '2409. 역삼동 디오슈페리움 (우성아파트 사거리)'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-290',
      'stationLatitude': '37.505329',
      'stationLongitude': '126.898483',
      'stationName': '241. 신길우성1차아파트 앞 공원'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1680',
      'stationLatitude': '37.499599',
      'stationLongitude': '127.033752',
      'stationName': '2410. 포스코피앤에스타워 (역삼역 3번출구 부근)'},
     {'parkingBikeTotCnt': '24',
      'rackTotCnt': '15',
      'shared': '160',
      'stationId': 'ST-1703',
      'stationLatitude': '37.472969',
      'stationLongitude': '127.112228',
      'stationName': '2411. 세곡동 성당'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '15',
      'shared': '100',
      'stationId': 'ST-1704',
      'stationLatitude': '37.491791',
      'stationLongitude': '127.088211',
      'stationName': '2412. 일원1동 주민센터'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-291',
      'stationLatitude': '37.510933',
      'stationLongitude': '126.910225',
      'stationName': '242. 신길선원가와인아파트 앞'},
     {'parkingBikeTotCnt': '27',
      'rackTotCnt': '15',
      'shared': '180',
      'stationId': 'ST-292',
      'stationLatitude': '37.527084',
      'stationLongitude': '126.891380',
      'stationName': '243. 이앤씨드림타워 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '20',
      'shared': '20',
      'stationId': 'ST-293',
      'stationLatitude': '37.530079',
      'stationLongitude': '126.905708',
      'stationName': '244. 영등포삼환아파트 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-294',
      'stationLatitude': '37.528263',
      'stationLongitude': '126.896629',
      'stationName': '245. 삼성생명 당산사옥 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-295',
      'stationLatitude': '37.533688',
      'stationLongitude': '126.902107',
      'stationName': '247. 당산역 10번출구 앞'},
     {'parkingBikeTotCnt': '28',
      'rackTotCnt': '10',
      'shared': '280',
      'stationId': 'ST-296',
      'stationLatitude': '37.531055',
      'stationLongitude': '126.924210',
      'stationName': '248. 초원아파트 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '8',
      'shared': '75',
      'stationId': 'ST-297',
      'stationLatitude': '37.524120',
      'stationLongitude': '126.936546',
      'stationName': '249. 여의도중학교 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-298',
      'stationLatitude': '37.507641',
      'stationLongitude': '126.923080',
      'stationName': '250. 대림아파트 사거리'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1552',
      'stationLatitude': '37.450661',
      'stationLongitude': '127.057060',
      'stationName': '2501. 서초 포레스타5단지'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '9',
      'shared': '33',
      'stationId': 'ST-1553',
      'stationLatitude': '37.491951',
      'stationLongitude': '127.008553',
      'stationName': '2502. 서초역1번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1554',
      'stationLatitude': '37.503811',
      'stationLongitude': '127.021362',
      'stationName': '2503. 반포1동 서초빌딩 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1555',
      'stationLatitude': '37.515881',
      'stationLongitude': '127.019302',
      'stationName': '2504. 신사역 4번출구 뒤'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '12',
      'shared': '33',
      'stationId': 'ST-1556',
      'stationLatitude': '37.493259',
      'stationLongitude': '127.029533',
      'stationName': '2505. 우성아파트사거리 (기업은행앞)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1557',
      'stationLatitude': '37.479092',
      'stationLongitude': '126.990677',
      'stationName': '2506. LG유플러스 (방배사옥)'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1654',
      'stationLatitude': '37.482979',
      'stationLongitude': '127.042259',
      'stationName': '2508. 양재이스타빌 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-299',
      'stationLatitude': '37.504494',
      'stationLongitude': '126.921951',
      'stationName': '251. 서울지방병무청 버스정류장'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1735',
      'stationLatitude': '37.483040',
      'stationLongitude': '127.021461',
      'stationName': '2510. JW타워'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '20',
      'shared': '95',
      'stationId': 'ST-1739',
      'stationLatitude': '37.483662',
      'stationLongitude': '126.982323',
      'stationName': '2511. 이수역 6번출구 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-300',
      'stationLatitude': '37.499828',
      'stationLongitude': '126.919945',
      'stationName': '252. 보라매역4번출구'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-301',
      'stationLatitude': '37.500648',
      'stationLongitude': '126.909515',
      'stationName': '253. 신풍역 5번출구 인근'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-302',
      'stationLatitude': '37.503803',
      'stationLongitude': '126.903419',
      'stationName': '254. 도림신협 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-303',
      'stationLatitude': '37.506573',
      'stationLongitude': '126.901131',
      'stationName': '255. 도림4거리'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-304',
      'stationLatitude': '37.509476',
      'stationLongitude': '126.899300',
      'stationName': '256. 동아에코빌입구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-305',
      'stationLatitude': '37.513844',
      'stationLongitude': '126.919357',
      'stationName': '257. 신길삼거리(우리은행)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '14',
      'shared': '0',
      'stationId': 'ST-306',
      'stationLatitude': '37.517693',
      'stationLongitude': '126.914299',
      'stationName': '258. 신길역3번출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '17',
      'shared': '6',
      'stationId': 'ST-307',
      'stationLatitude': '37.513592',
      'stationLongitude': '126.925934',
      'stationName': '259. 대방역6번출구'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '15',
      'shared': '113',
      'stationId': 'ST-414',
      'stationLatitude': '37.533680',
      'stationLongitude': '126.912086',
      'stationName': '260. 여의도 마리나선착장 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1590',
      'stationLatitude': '37.506748',
      'stationLongitude': '127.098831',
      'stationName': '2601. 석촌호수 서호사거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1592',
      'stationLatitude': '37.480801',
      'stationLongitude': '127.130341',
      'stationName': '2603. 송파 글마루 도서관'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1627',
      'stationLatitude': '37.531311',
      'stationLongitude': '127.111282',
      'stationName': '2604. 삼표레미콘 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1656',
      'stationLatitude': '37.471298',
      'stationLongitude': '127.127090',
      'stationName': '2605. 복정역 1번 출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1657',
      'stationLatitude': '37.481739',
      'stationLongitude': '127.143227',
      'stationName': '2606. 위례동주민센터 맞은편 근린공원'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1658',
      'stationLatitude': '37.470650',
      'stationLongitude': '127.127113',
      'stationName': '2607. 복정역 2번출구 후문 (장지치안센터)'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1681',
      'stationLatitude': '37.514359',
      'stationLongitude': '127.106194',
      'stationName': '2608. 송파구청'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1682',
      'stationLatitude': '37.520489',
      'stationLongitude': '127.135201',
      'stationName': '2609. 보성중고등학교 후문 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1683',
      'stationLatitude': '37.510441',
      'stationLongitude': '127.106377',
      'stationName': '2610. 여흥레이크빌 앞 (석촌호수 까페거리)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '7',
      'shared': '14',
      'stationId': 'ST-1684',
      'stationLatitude': '37.536331',
      'stationLongitude': '127.116180',
      'stationName': '2611. 송파지역자활센터 뒤'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1685',
      'stationLatitude': '37.489071',
      'stationLongitude': '127.109299',
      'stationName': '2612. 문정·가락 대여소 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '18',
      'shared': '22',
      'stationId': 'ST-1705',
      'stationLatitude': '37.516781',
      'stationLongitude': '127.090492',
      'stationName': '2613. 잠실나들목'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1706',
      'stationLatitude': '37.501862',
      'stationLongitude': '127.117233',
      'stationName': '2614. 가락고등학교 앞'},
     {'parkingBikeTotCnt': '27',
      'rackTotCnt': '15',
      'shared': '180',
      'stationId': 'ST-1707',
      'stationLatitude': '37.488350',
      'stationLongitude': '127.120781',
      'stationName': '2615. 테라타워2'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1716',
      'stationLatitude': '37.496078',
      'stationLongitude': '127.140106',
      'stationName': '2616. 거여동 사거리'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1717',
      'stationLatitude': '37.496181',
      'stationLongitude': '127.138031',
      'stationName': '2617. 가락삼환아파트 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '14',
      'shared': '0',
      'stationId': 'ST-1728',
      'stationLatitude': '37.504711',
      'stationLongitude': '127.087563',
      'stationName': '2618. 삼전역 1번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-1729',
      'stationLatitude': '37.502338',
      'stationLongitude': '127.096443',
      'stationName': '2619. 석촌고분역 4번출구'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '12',
      'shared': '108',
      'stationId': 'ST-416',
      'stationLatitude': '37.519928',
      'stationLongitude': '126.889183',
      'stationName': '262. 영문초등학교 사거리'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-1730',
      'stationLatitude': '37.509979',
      'stationLongitude': '127.112312',
      'stationName': '2620. 송파나루역 4번 출구옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1719',
      'stationLatitude': '37.516659',
      'stationLongitude': '127.116257',
      'stationName': '2621. 한성백제역 2번 출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1720',
      'stationLatitude': '37.516258',
      'stationLongitude': '127.130592',
      'stationName': '2622. 올림픽공원역 3번출구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '12',
      'shared': '75',
      'stationId': 'ST-417',
      'stationLatitude': '37.517151',
      'stationLongitude': '126.888626',
      'stationName': '263. 근로자회관 사거리'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-418',
      'stationLatitude': '37.521931',
      'stationLongitude': '126.891617',
      'stationName': '264. 교보생명보험 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-419',
      'stationLatitude': '37.521133',
      'stationLongitude': '126.896538',
      'stationName': '265. 영등포유통상가 사거리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-420',
      'stationLatitude': '37.520294',
      'stationLongitude': '126.901192',
      'stationName': '266. 영등포청과시장 사거리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-421',
      'stationLatitude': '37.535961',
      'stationLongitude': '126.898300',
      'stationName': '267. 삼성화재 사옥 옆'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '6',
      'shared': '100',
      'stationId': 'ST-422',
      'stationLatitude': '37.534718',
      'stationLongitude': '126.900002',
      'stationName': '268. 그랜드컨벤션센터 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-424',
      'stationLatitude': '37.522343',
      'stationLongitude': '126.927101',
      'stationName': '270. 증권거래소후문교차로'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1718',
      'stationLatitude': '37.565201',
      'stationLongitude': '126.827316',
      'stationName': '2701. 마곡나루역 5번출구 뒤편'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-1727',
      'stationLatitude': '37.569180',
      'stationLongitude': '126.819443',
      'stationName': '2702. 마곡 엠밸리2단지'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-425',
      'stationLatitude': '37.518963',
      'stationLongitude': '126.921616',
      'stationName': '271. 샛강생태공원방문자센터 앞'},
     {'parkingBikeTotCnt': '28',
      'rackTotCnt': '20',
      'shared': '140',
      'stationId': 'ST-426',
      'stationLatitude': '37.535339',
      'stationLongitude': '126.903679',
      'stationName': '272. 당산육갑문'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1319',
      'stationLatitude': '37.516651',
      'stationLongitude': '126.907990',
      'stationName': '274. 영등포역지하쇼핑센타 5번출구'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1320',
      'stationLatitude': '37.522816',
      'stationLongitude': '126.885651',
      'stationName': '275. 신동아아파트'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1321',
      'stationLatitude': '37.518284',
      'stationLongitude': '126.912636',
      'stationName': '276. SK 영등포주유소'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '10',
      'shared': '210',
      'stationId': 'ST-1322',
      'stationLatitude': '37.520119',
      'stationLongitude': '126.905167',
      'stationName': '277. 영등포뉴타운지하상가 2번게이트'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1323',
      'stationLatitude': '37.507931',
      'stationLongitude': '126.895233',
      'stationName': '278. 쌍용플레티넘오피스텔'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-1353',
      'stationLatitude': '37.513229',
      'stationLongitude': '126.904465',
      'stationName': '279. 영등포 푸르지오 아파트'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1539',
      'stationLatitude': '37.532101',
      'stationLongitude': '126.894440',
      'stationName': '280. 양평동6차현대아파트 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '8',
      'shared': '150',
      'stationId': 'ST-1540',
      'stationLatitude': '37.498241',
      'stationLongitude': '126.893982',
      'stationName': '281. 신동아아파트 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1541',
      'stationLatitude': '37.487530',
      'stationLongitude': '126.904877',
      'stationName': '282. 신한은행'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-1649',
      'stationLatitude': '37.522518',
      'stationLongitude': '126.907219',
      'stationName': '283. 아크로타워 스퀘어(영등포시장)'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '12',
      'shared': '33',
      'stationId': 'ST-1650',
      'stationLatitude': '37.518211',
      'stationLongitude': '126.902229',
      'stationName': '284. 센트럴 푸르지오 시티 앞'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '8',
      'shared': '288',
      'stationId': 'ST-1651',
      'stationLatitude': '37.499859',
      'stationLongitude': '126.897240',
      'stationName': '285. 대림3동사거리(하나은행)'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '8',
      'shared': '238',
      'stationId': 'ST-1652',
      'stationLatitude': '37.494572',
      'stationLongitude': '126.899750',
      'stationName': '286. 우성아파트 교차로'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1653',
      'stationLatitude': '37.525768',
      'stationLongitude': '126.905739',
      'stationName': '287. 영등포전화국사거리 (서강어린이공원)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1677',
      'stationLatitude': '37.528099',
      'stationLongitude': '126.893387',
      'stationName': '288. 쌍용예가(구청별관)'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1697',
      'stationLatitude': '37.499809',
      'stationLongitude': '126.898003',
      'stationName': '289. 대림3동사거리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '12',
      'shared': '17',
      'stationId': 'ST-1698',
      'stationLatitude': '37.531509',
      'stationLongitude': '126.897827',
      'stationName': '290. 당산동 SK V1 빌딩'},
     {'parkingBikeTotCnt': '28',
      'rackTotCnt': '14',
      'shared': '200',
      'stationId': 'ST-1699',
      'stationLatitude': '37.513851',
      'stationLongitude': '126.898880',
      'stationName': '291. 문래동 하이테크 시티'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1700',
      'stationLatitude': '37.510120',
      'stationLongitude': '126.904068',
      'stationName': '292. 영일 어린이공원'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '15',
      'shared': '80',
      'stationId': 'ST-1701',
      'stationLatitude': '37.529171',
      'stationLongitude': '126.907578',
      'stationName': '293. 충북 미래관'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '7',
      'shared': '214',
      'stationId': 'ST-116',
      'stationLatitude': '37.568050',
      'stationLongitude': '126.969231',
      'stationName': '300. 정동사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '16',
      'shared': '0',
      'stationId': 'ST-117',
      'stationLatitude': '37.575794',
      'stationLongitude': '126.971451',
      'stationName': '301. 경복궁역 7번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-118',
      'stationLatitude': '37.575947',
      'stationLongitude': '126.974060',
      'stationName': '302. 경복궁역 4번출구 뒤'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '8',
      'shared': '75',
      'stationId': 'ST-119',
      'stationLatitude': '37.571770',
      'stationLongitude': '126.974663',
      'stationName': '303. 광화문역 1번출구 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '7',
      'shared': '29',
      'stationId': 'ST-120',
      'stationLatitude': '37.572113',
      'stationLongitude': '126.977577',
      'stationName': '304. 광화문역 2번출구 앞'},
     {'parkingBikeTotCnt': '24',
      'rackTotCnt': '16',
      'shared': '150',
      'stationId': 'ST-121',
      'stationLatitude': '37.572582',
      'stationLongitude': '126.978355',
      'stationName': '305. 종로구청 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-122',
      'stationLatitude': '37.570808',
      'stationLongitude': '126.976433',
      'stationName': '306. 광화문역 7번출구 앞'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '11',
      'shared': '155',
      'stationId': 'ST-123',
      'stationLatitude': '37.570000',
      'stationLongitude': '126.971100',
      'stationName': '307. 서울역사박물관 앞'},
     {'parkingBikeTotCnt': '28',
      'rackTotCnt': '20',
      'shared': '140',
      'stationId': 'ST-124',
      'stationLatitude': '37.569969',
      'stationLongitude': '126.973938',
      'stationName': '308. 광화문 S타워 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '13',
      'shared': '38',
      'stationId': 'ST-125',
      'stationLatitude': '37.569889',
      'stationLongitude': '126.976456',
      'stationName': '309. 광화문역 6번출구 옆'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-126',
      'stationLatitude': '37.568878',
      'stationLongitude': '126.977470',
      'stationName': '310. 청계광장 옆'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-1188',
      'stationLatitude': '37.557396',
      'stationLongitude': '126.952164',
      'stationName': '3100. 북성초교'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-1189',
      'stationLatitude': '37.578381',
      'stationLongitude': '126.936096',
      'stationName': '3101. 서대문구청'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1190',
      'stationLatitude': '37.567966',
      'stationLongitude': '126.931725',
      'stationName': '3102. 연희삼거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1491',
      'stationLatitude': '37.586700',
      'stationLongitude': '126.946770',
      'stationName': '3103. 홍제삼거리 북측'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '13',
      'shared': '38',
      'stationId': 'ST-1492',
      'stationLatitude': '37.558128',
      'stationLongitude': '126.956207',
      'stationName': '3104. e편한세상 신촌4단지 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '12',
      'shared': '58',
      'stationId': 'ST-1493',
      'stationLatitude': '37.597149',
      'stationLongitude': '126.938530',
      'stationName': '3105. 홍은센트레빌 아파트 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '7',
      'shared': '0',
      'stationId': 'ST-1643',
      'stationLatitude': '37.574909',
      'stationLongitude': '126.926147',
      'stationName': '3106. 홍남교 두바퀴쉼터'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '7',
      'shared': '29',
      'stationId': 'ST-1644',
      'stationLatitude': '37.569740',
      'stationLongitude': '126.933327',
      'stationName': '3107. 연희초등학교 앞'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '35',
      'shared': '57',
      'stationId': 'ST-127',
      'stationLatitude': '37.566612',
      'stationLongitude': '126.977470',
      'stationName': '311. 서울광장 옆'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '7',
      'shared': '71',
      'stationId': 'ST-128',
      'stationLatitude': '37.564674',
      'stationLongitude': '126.976738',
      'stationName': '312. 시청역 1번출구 뒤'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '5',
      'shared': '60',
      'stationId': 'ST-129',
      'stationLatitude': '37.556961',
      'stationLongitude': '126.971771',
      'stationName': '313. 서울역 광장 파출소 옆'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-130',
      'stationLatitude': '37.579708',
      'stationLongitude': '126.980858',
      'stationName': '314. 국립현대미술관'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '9',
      'shared': '33',
      'stationId': 'ST-131',
      'stationLatitude': '37.575970',
      'stationLongitude': '126.983063',
      'stationName': '315. 신한은행 안국역지점 옆'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '12',
      'shared': '108',
      'stationId': 'ST-132',
      'stationLatitude': '37.570396',
      'stationLongitude': '126.981789',
      'stationName': '316. 종각역 1번출구 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-134',
      'stationLatitude': '37.568527',
      'stationLongitude': '126.982552',
      'stationName': '318. 광교사거리 남측'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '20',
      'shared': '80',
      'stationId': 'ST-136',
      'stationLatitude': '37.566223',
      'stationLongitude': '126.983589',
      'stationName': '320. 을지로입구역 4번출구 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '15',
      'shared': '100',
      'stationId': 'ST-137',
      'stationLatitude': '37.565464',
      'stationLongitude': '126.984138',
      'stationName': '321. KEB 하나금융그룹 명동사옥 옆'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-138',
      'stationLatitude': '37.564476',
      'stationLongitude': '126.986969',
      'stationName': '322. 명동성당 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-140',
      'stationLatitude': '37.561340',
      'stationLongitude': '126.980400',
      'stationName': '324. 신세계백화점 본점 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '19',
      'shared': '58',
      'stationId': 'ST-142',
      'stationLatitude': '37.576241',
      'stationLongitude': '126.986160',
      'stationName': '326. 안국역 5번출구 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-143',
      'stationLatitude': '37.573357',
      'stationLongitude': '126.987465',
      'stationName': '327. 낙원상가 옆'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '11',
      'shared': '18',
      'stationId': 'ST-144',
      'stationLatitude': '37.570396',
      'stationLongitude': '126.988190',
      'stationName': '328. 탑골공원 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '8',
      'shared': '113',
      'stationId': 'ST-145',
      'stationLatitude': '37.568344',
      'stationLongitude': '126.987892',
      'stationName': '329. 청계2가 사거리 옆'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '10',
      'shared': '170',
      'stationId': 'ST-146',
      'stationLatitude': '37.568165',
      'stationLongitude': '126.984978',
      'stationName': '330. 청계천 한빛광장'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-147',
      'stationLatitude': '37.566383',
      'stationLongitude': '126.987206',
      'stationName': '331. 을지로2가 사거리 북측'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '5',
      'shared': '0',
      'stationId': 'ST-148',
      'stationLatitude': '37.565990',
      'stationLongitude': '126.987793',
      'stationName': '332. 을지로2가 사거리 남측'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-150',
      'stationLatitude': '37.570599',
      'stationLongitude': '126.991791',
      'stationName': '334. 종로3가역 2번출구 뒤'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-151',
      'stationLatitude': '37.570198',
      'stationLongitude': '126.991257',
      'stationName': '335. 종로3가역 15번출구 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-152',
      'stationLatitude': '37.562618',
      'stationLongitude': '126.992836',
      'stationName': '336. 티마크 호텔 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '5',
      'shared': '20',
      'stationId': 'ST-153',
      'stationLatitude': '37.578979',
      'stationLongitude': '126.996475',
      'stationName': '337. 창경궁 입구'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '18',
      'shared': '111',
      'stationId': 'ST-154',
      'stationLatitude': '37.570957',
      'stationLongitude': '126.997124',
      'stationName': '338. 세운스퀘어 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-155',
      'stationLatitude': '37.571068',
      'stationLongitude': '126.998192',
      'stationName': '339. 종로4가 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-156',
      'stationLatitude': '37.585629',
      'stationLongitude': '127.000679',
      'stationName': '340. 혜화동 로터리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-157',
      'stationLatitude': '37.581570',
      'stationLongitude': '127.001785',
      'stationName': '341. 혜화역 3번출구 뒤'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-158',
      'stationLatitude': '37.579784',
      'stationLongitude': '127.002533',
      'stationName': '342. 대학로 마로니에공원'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-159',
      'stationLatitude': '37.575432',
      'stationLongitude': '127.004982',
      'stationName': '343. 예일빌딩(율곡로) 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-160',
      'stationLatitude': '37.574036',
      'stationLongitude': '127.006721',
      'stationName': '344. 성균관대 E하우스 앞'},
     {'parkingBikeTotCnt': '24',
      'rackTotCnt': '15',
      'shared': '160',
      'stationId': 'ST-161',
      'stationLatitude': '37.573307',
      'stationLongitude': '127.000710',
      'stationName': '345. 서울보증보험본사 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-162',
      'stationLatitude': '37.569183',
      'stationLongitude': '127.009880',
      'stationName': '346. 맥스타일 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '18',
      'shared': '78',
      'stationId': 'ST-163',
      'stationLatitude': '37.565331',
      'stationLongitude': '127.007843',
      'stationName': '347. 동대문역사문화공원역 9번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '14',
      'shared': '0',
      'stationId': 'ST-183',
      'stationLatitude': '37.572029',
      'stationLongitude': '126.960785',
      'stationName': '348. 독립문역 사거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '7',
      'shared': '14',
      'stationId': 'ST-165',
      'stationLatitude': '37.576332',
      'stationLongitude': '126.968590',
      'stationName': '349. 사직동주민센터'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1191',
      'stationLatitude': '37.537014',
      'stationLongitude': '127.061096',
      'stationName': '3506. 영동대교 북단'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '25',
      'shared': '0',
      'stationId': 'ST-1192',
      'stationLatitude': '37.545952',
      'stationLongitude': '127.078003',
      'stationName': '3507. 어린이회관'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1193',
      'stationLatitude': '37.548222',
      'stationLongitude': '127.067879',
      'stationName': '3508. 화양사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-1194',
      'stationLatitude': '37.553417',
      'stationLongitude': '127.073196',
      'stationName': '3509. 세종사이버대학교'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '8',
      'shared': '75',
      'stationId': 'ST-167',
      'stationLatitude': '37.585079',
      'stationLongitude': '126.970619',
      'stationName': '351. 청운초교 앞 삼거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1427',
      'stationLatitude': '37.568649',
      'stationLongitude': '127.086250',
      'stationName': '3510. 중곡SK아파트앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1195',
      'stationLatitude': '37.551250',
      'stationLongitude': '127.035103',
      'stationName': '3511. 응봉역 1번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1197',
      'stationLatitude': '37.564610',
      'stationLongitude': '127.029198',
      'stationName': '3513. 상왕십리역 1번출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1198',
      'stationLatitude': '37.566261',
      'stationLongitude': '127.023697',
      'stationName': '3514. 왕십리교회옆'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '20',
      'shared': '45',
      'stationId': 'ST-1199',
      'stationLatitude': '37.542816',
      'stationLongitude': '127.042084',
      'stationName': '3515. 서울숲 관리사무소'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '10',
      'shared': '160',
      'stationId': 'ST-1266',
      'stationLatitude': '37.562527',
      'stationLongitude': '127.082275',
      'stationName': '3517. 용마사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1263',
      'stationLatitude': '37.556862',
      'stationLongitude': '127.079140',
      'stationName': '3518. 군자역 7번출구뒤'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1336',
      'stationLatitude': '37.562607',
      'stationLongitude': '127.051308',
      'stationName': '3519. 용답역 1번 출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-168',
      'stationLatitude': '37.583416',
      'stationLongitude': '126.985237',
      'stationName': '352. 중앙고입구 삼거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1378',
      'stationLatitude': '37.542519',
      'stationLongitude': '127.084084',
      'stationName': '3520. 광진경찰서'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1379',
      'stationLatitude': '37.543427',
      'stationLongitude': '127.096619',
      'stationName': '3521. 현대홈타운 뒷길'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '9',
      'shared': '89',
      'stationId': 'ST-1377',
      'stationLatitude': '37.561245',
      'stationLongitude': '127.048851',
      'stationName': '3522. 사근삼거리'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1429',
      'stationLatitude': '37.541718',
      'stationLongitude': '127.080170',
      'stationName': '3523. 건국대학교 과학관(이과대) 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1428',
      'stationLatitude': '37.550236',
      'stationLongitude': '127.073822',
      'stationName': '3524. 세종대학교'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '15',
      'shared': '133',
      'stationId': 'ST-1599',
      'stationLatitude': '37.546089',
      'stationLongitude': '127.025070',
      'stationName': '3525. 금호스포츠센터앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1601',
      'stationLatitude': '37.561790',
      'stationLongitude': '127.024391',
      'stationName': '3527. 왕십리 자이아파트'},
     {'parkingBikeTotCnt': '25',
      'rackTotCnt': '8',
      'shared': '313',
      'stationId': 'ST-1602',
      'stationLatitude': '37.550598',
      'stationLongitude': '127.110512',
      'stationName': '3528. 광진정보도서관'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1603',
      'stationLatitude': '37.549789',
      'stationLongitude': '127.075928',
      'stationName': '3529. 어린이대공원정문'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-169',
      'stationLatitude': '37.579388',
      'stationLongitude': '126.984947',
      'stationName': '353. 재동초교 앞 삼거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1616',
      'stationLatitude': '37.560146',
      'stationLongitude': '127.026360',
      'stationName': '3530. 왕십리자이아파트 후문(삼거리)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-1617',
      'stationLatitude': '37.554779',
      'stationLongitude': '127.024841',
      'stationName': '3531. 논골사거리(금호도서관 입구)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-1618',
      'stationLatitude': '37.560680',
      'stationLongitude': '127.026779',
      'stationName': '3532. 왕십리KCC스위첸아파트'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1660',
      'stationLatitude': '37.539139',
      'stationLongitude': '127.070618',
      'stationName': '3533. 건대입구역 사거리(롯데백화점)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '12',
      'shared': '17',
      'stationId': 'ST-1661',
      'stationLatitude': '37.540138',
      'stationLongitude': '127.069283',
      'stationName': '3534. 건대입구역 5번출구 뒤'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1662',
      'stationLatitude': '37.559158',
      'stationLongitude': '127.087517',
      'stationName': '3535. 중곡사거리(국민은행)'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1663',
      'stationLatitude': '37.531811',
      'stationLongitude': '127.080742',
      'stationName': '3536. 중앙농협(자양동)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1664',
      'stationLatitude': '37.548489',
      'stationLongitude': '127.093758',
      'stationName': '3537. 아차산 휴먼시아 아파트 옆'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '14',
      'shared': '57',
      'stationId': 'ST-1659',
      'stationLatitude': '37.550892',
      'stationLongitude': '127.044762',
      'stationName': '3538. 서울숲 IT캐슬'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1686',
      'stationLatitude': '37.563820',
      'stationLongitude': '127.132843',
      'stationName': '3539. 서원마을'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-170',
      'stationLatitude': '37.579155',
      'stationLongitude': '126.988960',
      'stationName': '354. 포르투갈 대사관 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-1690',
      'stationLatitude': '37.541248',
      'stationLongitude': '127.066040',
      'stationName': '3541. 커먼그라운드'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '17',
      'shared': '0',
      'stationId': 'ST-1722',
      'stationLatitude': '37.545040',
      'stationLongitude': '127.089958',
      'stationName': '3542. 래미안 구의파크 스위트'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-171',
      'stationLatitude': '37.576508',
      'stationLongitude': '127.002457',
      'stationName': '355. 서울사대부속초교 앞'},
     {'parkingBikeTotCnt': '24',
      'rackTotCnt': '15',
      'shared': '160',
      'stationId': 'ST-172',
      'stationLatitude': '37.577145',
      'stationLongitude': '127.002060',
      'stationName': '356. KT혜화지사 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '13',
      'shared': '0',
      'stationId': 'ST-173',
      'stationLatitude': '37.582500',
      'stationLongitude': '126.998535',
      'stationName': '358. 성대입구 사거리'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '8',
      'shared': '163',
      'stationId': 'ST-174',
      'stationLatitude': '37.576061',
      'stationLongitude': '126.997681',
      'stationName': '359. 원남동사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-175',
      'stationLatitude': '37.573242',
      'stationLongitude': '127.015907',
      'stationName': '361. 동묘앞역 1번출구 뒤'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-176',
      'stationLatitude': '37.572224',
      'stationLongitude': '127.022705',
      'stationName': '362. 청계8가 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-177',
      'stationLatitude': '37.575760',
      'stationLongitude': '127.022835',
      'stationName': '363. 신설동역 11번출구 뒤'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-178',
      'stationLatitude': '37.579334',
      'stationLongitude': '127.015083',
      'stationName': '364. 창신역 1번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-180',
      'stationLatitude': '37.573849',
      'stationLongitude': '126.958694',
      'stationName': '367. 독립문역 3-1번출구 '},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '12',
      'shared': '117',
      'stationId': 'ST-181',
      'stationLatitude': '37.569248',
      'stationLongitude': '126.980537',
      'stationName': '368. SK 서린빌딩 앞'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '20',
      'shared': '40',
      'stationId': 'ST-182',
      'stationLatitude': '37.575493',
      'stationLongitude': '126.978500',
      'stationName': '369. 광화문 시민열린마당'},
     {'parkingBikeTotCnt': '35',
      'rackTotCnt': '26',
      'shared': '135',
      'stationId': 'ST-185',
      'stationLatitude': '37.563229',
      'stationLongitude': '126.974838',
      'stationName': '370. 시청역(2호선) 9번출구 뒤'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-186',
      'stationLatitude': '37.558872',
      'stationLongitude': '127.005539',
      'stationName': '371. 동대입구역 6번출구 뒤'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-187',
      'stationLatitude': '37.554295',
      'stationLongitude': '127.011200',
      'stationName': '372. 약수역 3번출구 뒤'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-188',
      'stationLatitude': '37.555859',
      'stationLongitude': '127.013855',
      'stationName': '373. 청구 어린이공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-189',
      'stationLatitude': '37.560474',
      'stationLongitude': '127.014076',
      'stationName': '374. 청구역 2번출구 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-190',
      'stationLatitude': '37.563717',
      'stationLongitude': '127.018425',
      'stationName': '375. 다산 어린이공원'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-193',
      'stationLatitude': '37.569805',
      'stationLongitude': '127.016953',
      'stationName': '378. 청계7가 사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '7',
      'shared': '57',
      'stationId': 'ST-194',
      'stationLatitude': '37.556000',
      'stationLongitude': '126.973358',
      'stationName': '379. 서울역9번출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-195',
      'stationLatitude': '37.563866',
      'stationLongitude': '127.002747',
      'stationName': '380. CJ제일제당 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-196',
      'stationLatitude': '37.558533',
      'stationLongitude': '127.006989',
      'stationName': '381. 장충체육관'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '7',
      'shared': '129',
      'stationId': 'ST-197',
      'stationLatitude': '37.555199',
      'stationLongitude': '127.010048',
      'stationName': '382. 약수역 10번출구 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '17',
      'shared': '29',
      'stationId': 'ST-198',
      'stationLatitude': '37.565849',
      'stationLongitude': '127.016403',
      'stationName': '383. 신당역 12번 출구 뒤'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-199',
      'stationLatitude': '37.559780',
      'stationLongitude': '126.968506',
      'stationName': '384. 종로학원본원 '},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-336',
      'stationLatitude': '37.569836',
      'stationLongitude': '126.982658',
      'stationName': '385. 종각역 5번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-337',
      'stationLatitude': '37.590233',
      'stationLongitude': '126.998520',
      'stationName': '386. 올림픽기념 국민생활관 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-338',
      'stationLatitude': '37.566994',
      'stationLongitude': '127.003464',
      'stationName': '387. 훈련원공원주차장 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-444',
      'stationLatitude': '37.585735',
      'stationLongitude': '127.001610',
      'stationName': '388. 동성중학교 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1372',
      'stationLatitude': '37.570141',
      'stationLongitude': '127.009377',
      'stationName': '393. 동대문역 8번 출구'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1373',
      'stationLatitude': '37.567490',
      'stationLongitude': '126.965919',
      'stationName': '394. 경희궁 자이 3단지'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '8',
      'shared': '88',
      'stationId': 'ST-1374',
      'stationLatitude': '37.568855',
      'stationLongitude': '126.964561',
      'stationName': '395. 경희궁 자이 2단지'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '13',
      'shared': '54',
      'stationId': 'ST-1432',
      'stationLatitude': '37.570480',
      'stationLongitude': '126.996635',
      'stationName': '397. 종묘공영주차장 건너편'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '8',
      'shared': '88',
      'stationId': 'ST-1435',
      'stationLatitude': '37.566559',
      'stationLongitude': '126.992439',
      'stationName': '398. 을지로3가역 3번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1436',
      'stationLatitude': '37.554108',
      'stationLongitude': '126.965408',
      'stationName': '399. 서울역 센트럴 자이아파트'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-110',
      'stationLatitude': '37.587524',
      'stationLongitude': '126.883003',
      'stationName': '400. 상암한화오벨리스크 1차 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '10',
      'shared': '150',
      'stationId': 'ST-1397',
      'stationLatitude': '37.569584',
      'stationLongitude': '126.903816',
      'stationName': '427. 성산시영아파트'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-1437',
      'stationLatitude': '37.564400',
      'stationLongitude': '126.991432',
      'stationName': '428. 명보사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-1438',
      'stationLatitude': '37.549889',
      'stationLongitude': '127.007347',
      'stationName': '429. 송도병원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '8',
      'shared': '50',
      'stationId': 'ST-1439',
      'stationLatitude': '37.562172',
      'stationLongitude': '127.006264',
      'stationName': '430. KEB하나은행 장충동지점'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1440',
      'stationLatitude': '37.570900',
      'stationLongitude': '127.019524',
      'stationName': '431. 청계천 영도교'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1494',
      'stationLatitude': '37.563339',
      'stationLongitude': '126.908203',
      'stationName': '432. 마포중앙도서관'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1668',
      'stationLatitude': '37.566345',
      'stationLongitude': '126.982292',
      'stationName': '433. 을지로입구역 2번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1669',
      'stationLatitude': '37.561489',
      'stationLongitude': '127.023933',
      'stationName': '434. 신당 레미안 버스정류장'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1670',
      'stationLatitude': '37.556862',
      'stationLongitude': '126.975616',
      'stationName': '435. SK 남산빌딩'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1675',
      'stationLatitude': '37.556591',
      'stationLongitude': '126.946190',
      'stationName': '436. 이대역 5번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '12',
      'shared': '50',
      'stationId': 'ST-1691',
      'stationLatitude': '37.548210',
      'stationLongitude': '126.941383',
      'stationName': '437. 대흥역 1번출구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1692',
      'stationLatitude': '37.564720',
      'stationLongitude': '126.906769',
      'stationName': '438. 성산2-1 공영주차장'},
     {'parkingBikeTotCnt': '35',
      'rackTotCnt': '10',
      'shared': '350',
      'stationId': 'ST-1693',
      'stationLatitude': '37.535751',
      'stationLongitude': '126.944038',
      'stationName': '439. 마포어린이공원'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '13',
      'shared': '46',
      'stationId': 'ST-1605',
      'stationLatitude': '37.571239',
      'stationLongitude': '127.004410',
      'stationName': '452. 동대문 종합시장 버스정류장'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1606',
      'stationLatitude': '37.571140',
      'stationLongitude': '127.000671',
      'stationName': '453. 종로오가 지하쇼핑센터 14번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '13',
      'shared': '46',
      'stationId': 'ST-1607',
      'stationLatitude': '37.570358',
      'stationLongitude': '126.986382',
      'stationName': '454. 종로2가 버스정류장 (종각방향)'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '8',
      'shared': '163',
      'stationId': 'ST-1608',
      'stationLatitude': '37.570961',
      'stationLongitude': '127.006058',
      'stationName': '455. 삼익한의원'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1609',
      'stationLatitude': '37.574471',
      'stationLongitude': '127.019829',
      'stationName': '456. 숭인2동 주민센터 입구 (이강3대냉면)'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1610',
      'stationLatitude': '37.571320',
      'stationLongitude': '127.007210',
      'stationName': '457. 종로꽃시장 입구 옆'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '11',
      'shared': '55',
      'stationId': 'ST-1611',
      'stationLatitude': '37.569939',
      'stationLongitude': '126.977539',
      'stationName': '458. 광화문역 5번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1619',
      'stationLatitude': '37.574364',
      'stationLongitude': '126.972366',
      'stationName': '461. 서울지방경찰청'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1752',
      'stationLatitude': '37.603512',
      'stationLongitude': '126.962067',
      'stationName': '462. 신영동삼거리(북악터널방향)'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-100',
      'stationLatitude': '37.536667',
      'stationLongitude': '127.073593',
      'stationName': '503. 더샵스타시티 C동 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '9',
      'shared': '0',
      'stationId': 'ST-101',
      'stationLatitude': '37.532970',
      'stationLongitude': '127.075935',
      'stationName': '504. 신자초교입구교차로'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-102',
      'stationLatitude': '37.537010',
      'stationLongitude': '127.082245',
      'stationName': '505. 자양사거리 광진아크로텔 앞'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '7',
      'shared': '257',
      'stationId': 'ST-103',
      'stationLatitude': '37.549061',
      'stationLongitude': '127.057793',
      'stationName': '506. 금호 어울림 아파트 앞'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '7',
      'shared': '300',
      'stationId': 'ST-104',
      'stationLatitude': '37.548203',
      'stationLongitude': '127.057114',
      'stationName': '507. 성수아이에스비즈타워 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-105',
      'stationLatitude': '37.545166',
      'stationLongitude': '127.057510',
      'stationName': '508. 성수아카데미타워 앞'},
     {'parkingBikeTotCnt': '68',
      'rackTotCnt': '20',
      'shared': '340',
      'stationId': 'ST-106',
      'stationLatitude': '37.539654',
      'stationLongitude': '127.052589',
      'stationName': '509. 이마트 버스정류소 옆'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-107',
      'stationLatitude': '37.541222',
      'stationLongitude': '127.043800',
      'stationName': '510. 서울숲 남문 버스정류소 옆'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '16',
      'shared': '50',
      'stationId': 'ST-108',
      'stationLatitude': '37.544582',
      'stationLongitude': '127.044609',
      'stationName': '511. 서울숲역 4번 출구 옆'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-109',
      'stationLatitude': '37.548561',
      'stationLongitude': '127.045006',
      'stationName': '512. 뚝섬역 1번 출구 옆'},
     {'parkingBikeTotCnt': '29',
      'rackTotCnt': '13',
      'shared': '223',
      'stationId': 'ST-111',
      'stationLatitude': '37.546307',
      'stationLongitude': '127.049805',
      'stationName': '513. 뚝섬역 5번 출구 정류소 옆'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '7',
      'shared': '43',
      'stationId': 'ST-112',
      'stationLatitude': '37.542580',
      'stationLongitude': '127.063309',
      'stationName': '514. 성수사거리 버스정류장 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-113',
      'stationLatitude': '37.530235',
      'stationLongitude': '127.086830',
      'stationName': '515. 광양중학교 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-114',
      'stationLatitude': '37.548405',
      'stationLongitude': '127.069366',
      'stationName': '516. 광진메디칼 앞'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '20',
      'shared': '75',
      'stationId': 'ST-234',
      'stationLatitude': '37.571526',
      'stationLongitude': '127.035355',
      'stationName': '518. 청계천 박물관 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '20',
      'shared': '25',
      'stationId': 'ST-235',
      'stationLatitude': '37.566994',
      'stationLongitude': '127.029915',
      'stationName': '519. 양지사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-236',
      'stationLatitude': '37.563858',
      'stationLongitude': '127.030319',
      'stationName': '520. 상왕십리역 4번 출구 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '14',
      'shared': '14',
      'stationId': 'ST-237',
      'stationLatitude': '37.561447',
      'stationLongitude': '127.034920',
      'stationName': '521. 왕십리역 11번 출구 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '9',
      'shared': '56',
      'stationId': 'ST-238',
      'stationLatitude': '37.548641',
      'stationLongitude': '127.016426',
      'stationName': '522. 금호역 1번출구 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '11',
      'shared': '36',
      'stationId': 'ST-239',
      'stationLatitude': '37.543663',
      'stationLongitude': '127.014061',
      'stationName': '523. 옥수동성당 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-240',
      'stationLatitude': '37.552200',
      'stationLongitude': '127.025055',
      'stationName': '524. 래미안금호하이리버 아파트 102동 옆'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-241',
      'stationLatitude': '37.558052',
      'stationLongitude': '127.040352',
      'stationName': '525. 한양대병원사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-242',
      'stationLatitude': '37.563511',
      'stationLongitude': '127.056725',
      'stationName': '526. 용답토속공원 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '15',
      'shared': '13',
      'stationId': 'ST-243',
      'stationLatitude': '37.561371',
      'stationLongitude': '127.063660',
      'stationName': '529. 장한평역 8번 출구 앞'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '9',
      'shared': '200',
      'stationId': 'ST-244',
      'stationLatitude': '37.568748',
      'stationLongitude': '127.030403',
      'stationName': '530. 청계벽산아파트 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '7',
      'shared': '157',
      'stationId': 'ST-245',
      'stationLatitude': '37.548149',
      'stationLongitude': '127.021088',
      'stationName': '533. 우리은행 금호동 지점 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-246',
      'stationLatitude': '37.548634',
      'stationLongitude': '127.025726',
      'stationName': '534. 금호사거리'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '16',
      'shared': '88',
      'stationId': 'ST-247',
      'stationLatitude': '37.553986',
      'stationLongitude': '127.033592',
      'stationName': '535. 응봉삼거리'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '8',
      'shared': '63',
      'stationId': 'ST-248',
      'stationLatitude': '37.557350',
      'stationLongitude': '127.029213',
      'stationName': '536. 행당역 2번출구 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-249',
      'stationLatitude': '37.560356',
      'stationLongitude': '127.041397',
      'stationName': '537. 한양대후문역 부근'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-250',
      'stationLatitude': '37.567650',
      'stationLongitude': '127.051155',
      'stationName': '538. 답십리역 8번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '8',
      'shared': '0',
      'stationId': 'ST-253',
      'stationLatitude': '37.556030',
      'stationLongitude': '127.078644',
      'stationName': '540. 군자역 7번출구 베스트샵 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '19',
      'shared': '63',
      'stationId': 'ST-254',
      'stationLatitude': '37.535465',
      'stationLongitude': '127.094482',
      'stationName': '542. 강변역 4번출구 뒤'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '20',
      'shared': '45',
      'stationId': 'ST-255',
      'stationLatitude': '37.535969',
      'stationLongitude': '127.094673',
      'stationName': '543. 구의공원(테크노마트 앞)'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '20',
      'shared': '55',
      'stationId': 'ST-256',
      'stationLatitude': '37.540730',
      'stationLongitude': '127.102905',
      'stationName': '544. 광남중학교'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-257',
      'stationLatitude': '37.532478',
      'stationLongitude': '127.085091',
      'stationName': '546. 잠실대교북단 교차로'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-258',
      'stationLatitude': '37.529770',
      'stationLongitude': '127.074860',
      'stationName': '548. 자양나들목'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-259',
      'stationLatitude': '37.551224',
      'stationLongitude': '127.089706',
      'stationName': '549. 아차산역 3번출구'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '15',
      'shared': '133',
      'stationId': 'ST-251',
      'stationLatitude': '37.571640',
      'stationLongitude': '127.035660',
      'stationName': '550. 서울시설공단 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-377',
      'stationLatitude': '37.540062',
      'stationLongitude': '127.094498',
      'stationName': '551. 구의삼성쉐르빌 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-378',
      'stationLatitude': '37.536579',
      'stationLongitude': '127.092972',
      'stationName': '552. 대림아크로리버 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-379',
      'stationLatitude': '37.571255',
      'stationLongitude': '127.079803',
      'stationName': '553. 중곡 성원APT 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-381',
      'stationLatitude': '37.537849',
      'stationLongitude': '127.092171',
      'stationName': '555. 구의3동주민센터'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-357',
      'stationLatitude': '37.542053',
      'stationLongitude': '127.020401',
      'stationName': '556. 달맞이공원'},
     {'parkingBikeTotCnt': '26',
      'rackTotCnt': '10',
      'shared': '260',
      'stationId': 'ST-358',
      'stationLatitude': '37.567642',
      'stationLongitude': '127.025696',
      'stationName': '557. 도선동 주민센터 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '20',
      'shared': '35',
      'stationId': 'ST-359',
      'stationLatitude': '37.564606',
      'stationLongitude': '127.036522',
      'stationName': '558. 성동광진 교육지원청 앞'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-360',
      'stationLatitude': '37.561096',
      'stationLongitude': '127.036797',
      'stationName': '559. 왕십리역 4번 출구 건너편'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '8',
      'shared': '63',
      'stationId': 'ST-361',
      'stationLatitude': '37.551205',
      'stationLongitude': '127.068932',
      'stationName': '560. 비전교회 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-362',
      'stationLatitude': '37.542816',
      'stationLongitude': '127.044670',
      'stationName': '561. 서울숲역 2번출구 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-363',
      'stationLatitude': '37.559246',
      'stationLongitude': '127.073410',
      'stationName': '562. 군자지하보도 앞'},
     {'parkingBikeTotCnt': '58',
      'rackTotCnt': '10',
      'shared': '580',
      'stationId': 'ST-364',
      'stationLatitude': '37.547913',
      'stationLongitude': '127.062752',
      'stationName': '563. 성동세무서 건너편'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-365',
      'stationLatitude': '37.547928',
      'stationLongitude': '127.015572',
      'stationName': '564. 금호역 3번출구'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '20',
      'shared': '90',
      'stationId': 'ST-366',
      'stationLatitude': '37.541363',
      'stationLongitude': '127.017662',
      'stationName': '565. 옥수역 3번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '15',
      'shared': '40',
      'stationId': 'ST-368',
      'stationLatitude': '37.544590',
      'stationLongitude': '127.057083',
      'stationName': '567. 성수역 2번출구 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-369',
      'stationLatitude': '37.571102',
      'stationLongitude': '127.023560',
      'stationName': '568. 청계8가사거리 부근'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-370',
      'stationLatitude': '37.549583',
      'stationLongitude': '127.030243',
      'stationName': '569. 응봉현대아파트 정류소'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-382',
      'stationLatitude': '37.548496',
      'stationLongitude': '127.074760',
      'stationName': '571. 어린이대공원역6번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '20',
      'shared': '30',
      'stationId': 'ST-383',
      'stationLatitude': '37.565380',
      'stationLongitude': '127.086510',
      'stationName': '572. 국립정신 건강센터 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-384',
      'stationLatitude': '37.545231',
      'stationLongitude': '127.084732',
      'stationName': '573. 구의문주차장 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-385',
      'stationLatitude': '37.551849',
      'stationLongitude': '127.088982',
      'stationName': '574. 아차산역4번출구'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-386',
      'stationLatitude': '37.564293',
      'stationLongitude': '127.086937',
      'stationName': '575. 중앙농협 중곡지점'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-387',
      'stationLatitude': '37.544830',
      'stationLongitude': '127.104263',
      'stationName': '576. 광나루역 3번 출구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-388',
      'stationLatitude': '37.546547',
      'stationLongitude': '127.106133',
      'stationName': '577. 광진청소년수련관'},
     {'parkingBikeTotCnt': '40',
      'rackTotCnt': '8',
      'shared': '500',
      'stationId': 'ST-371',
      'stationLatitude': '37.548286',
      'stationLongitude': '127.062088',
      'stationName': '578. 성동세무서 부근'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '8',
      'shared': '88',
      'stationId': 'ST-372',
      'stationLatitude': '37.565205',
      'stationLongitude': '127.041847',
      'stationName': '579. 마장역 4번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '6',
      'shared': '0',
      'stationId': 'ST-373',
      'stationLatitude': '37.554493',
      'stationLongitude': '127.020210',
      'stationName': '580. 신금호역 3번출구 뒤'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '13',
      'shared': '38',
      'stationId': 'ST-374',
      'stationLatitude': '37.561012',
      'stationLongitude': '127.054237',
      'stationName': '581. 용답초등학교'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-375',
      'stationLatitude': '37.543179',
      'stationLongitude': '127.049080',
      'stationName': '582. 경일중학교 앞'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '20',
      'shared': '100',
      'stationId': 'ST-376',
      'stationLatitude': '37.567970',
      'stationLongitude': '127.046890',
      'stationName': '583. 청계천 생태교실 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-445',
      'stationLatitude': '37.547829',
      'stationLongitude': '127.072632',
      'stationName': '584. 광진광장 교통섬'},
     {'parkingBikeTotCnt': '23',
      'rackTotCnt': '9',
      'shared': '256',
      'stationId': 'ST-446',
      'stationLatitude': '37.536808',
      'stationLongitude': '127.055489',
      'stationName': '585. 성수2가1동 공영주차장 인근'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-447',
      'stationLatitude': '37.565941',
      'stationLongitude': '127.045395',
      'stationName': '586. 마장동 주민센터'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-260',
      'stationLatitude': '37.589912',
      'stationLongitude': '127.068680',
      'stationName': '600. 휘경2동 주민센터'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-261',
      'stationLatitude': '37.575947',
      'stationLongitude': '127.037361',
      'stationName': '601. 용신동주민센터'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-262',
      'stationLatitude': '37.572174',
      'stationLongitude': '127.071388',
      'stationName': '602. 장안동 사거리'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '15',
      'shared': '107',
      'stationId': 'ST-264',
      'stationLatitude': '37.569656',
      'stationLongitude': '127.055962',
      'stationName': '604. 답십리초등학교 옆 공원'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '8',
      'shared': '200',
      'stationId': 'ST-265',
      'stationLatitude': '37.574200',
      'stationLongitude': '127.026497',
      'stationName': '605. 신설동역8번출구'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '15',
      'shared': '127',
      'stationId': 'ST-266',
      'stationLatitude': '37.584625',
      'stationLongitude': '127.070290',
      'stationName': '606. 휘경공고앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-267',
      'stationLatitude': '37.602711',
      'stationLongitude': '127.067863',
      'stationName': '607. 신이문역 2번출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-268',
      'stationLatitude': '37.581310',
      'stationLongitude': '127.055344',
      'stationName': '608. 전농삼성아파트'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '20',
      'shared': '20',
      'stationId': 'ST-269',
      'stationLatitude': '37.587791',
      'stationLongitude': '127.037361',
      'stationName': '609. 제기2교'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-270',
      'stationLatitude': '37.573086',
      'stationLongitude': '127.052162',
      'stationName': '610. 동대문중 교차로'},
     {'parkingBikeTotCnt': '30',
      'rackTotCnt': '20',
      'shared': '150',
      'stationId': 'ST-271',
      'stationLatitude': '37.573666',
      'stationLongitude': '127.030815',
      'stationName': '612. 시립동부병원 앞 사거리'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-272',
      'stationLatitude': '37.575272',
      'stationLongitude': '127.023468',
      'stationName': '613. 신설동역 10번출구 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-273',
      'stationLatitude': '37.577686',
      'stationLongitude': '127.031013',
      'stationName': '614. 용두동 사거리'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '20',
      'shared': '5',
      'stationId': 'ST-274',
      'stationLatitude': '37.576382',
      'stationLongitude': '127.035110',
      'stationName': '615. 용두동 레미안허브리츠아파트 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-275',
      'stationLatitude': '37.582561',
      'stationLongitude': '127.054367',
      'stationName': '616. 서울시립대 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-276',
      'stationLatitude': '37.574203',
      'stationLongitude': '127.057693',
      'stationName': '617. 청솔우성아파트 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '13',
      'shared': '0',
      'stationId': 'ST-389',
      'stationLatitude': '37.574718',
      'stationLongitude': '127.053391',
      'stationName': '621. 동대문중학교 옆'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '15',
      'shared': '120',
      'stationId': 'ST-390',
      'stationLatitude': '37.577793',
      'stationLongitude': '127.057831',
      'stationName': '622. 전농사거리 교통섬'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '20',
      'shared': '45',
      'stationId': 'ST-391',
      'stationLatitude': '37.583698',
      'stationLongitude': '127.053856',
      'stationName': '623. 서울시립대 정문 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-392',
      'stationLatitude': '37.574188',
      'stationLongitude': '127.045891',
      'stationName': '624. 전농동 동아아파트 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '9',
      'shared': '22',
      'stationId': 'ST-393',
      'stationLatitude': '37.568192',
      'stationLongitude': '127.057175',
      'stationName': '625. 답십리초등학교 앞(현대시장 옆)'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-394',
      'stationLatitude': '37.561153',
      'stationLongitude': '127.070969',
      'stationName': '626. 군자교 서측 녹지대'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-395',
      'stationLatitude': '37.578632',
      'stationLongitude': '127.071907',
      'stationName': '627. 장안동삼거리 교통섬'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-396',
      'stationLatitude': '37.586815',
      'stationLongitude': '127.067543',
      'stationName': '628. 휘봉고등학교 앞'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-397',
      'stationLatitude': '37.574852',
      'stationLongitude': '127.040306',
      'stationName': '630. 동대문구 보건소'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '15',
      'shared': '80',
      'stationId': 'ST-398',
      'stationLatitude': '37.568184',
      'stationLongitude': '127.051277',
      'stationName': '631. 답십리역 1번출구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '8',
      'shared': '113',
      'stationId': 'ST-400',
      'stationLatitude': '37.580406',
      'stationLongitude': '127.044823',
      'stationName': '633. 청량리 기업은행 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-401',
      'stationLatitude': '37.596020',
      'stationLongitude': '127.059830',
      'stationName': '634. 외국어대 정문 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '12',
      'shared': '0',
      'stationId': 'ST-402',
      'stationLatitude': '37.587517',
      'stationLongitude': '127.052773',
      'stationName': '635. 시조사 앞 (청량고정문 옆)'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '9',
      'shared': '233',
      'stationId': 'ST-403',
      'stationLatitude': '37.590900',
      'stationLongitude': '127.042587',
      'stationName': '636. 세종대왕기념관 교차로'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-404',
      'stationLatitude': '37.591614',
      'stationLongitude': '127.045792',
      'stationName': '637. KAIST 경영대학 앞'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '20',
      'shared': '40',
      'stationId': 'ST-405',
      'stationLatitude': '37.583008',
      'stationLongitude': '127.060974',
      'stationName': '638. 서울시립대 정보기술관'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '14',
      'shared': '7',
      'stationId': 'ST-406',
      'stationLatitude': '37.585197',
      'stationLongitude': '127.060951',
      'stationName': '639. 서울시립대 후문'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '6',
      'shared': '133',
      'stationId': 'ST-407',
      'stationLatitude': '37.582455',
      'stationLongitude': '127.044495',
      'stationName': '640. KEB하나은행 청량리역지점'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-408',
      'stationLatitude': '37.573753',
      'stationLongitude': '127.038536',
      'stationName': '641. 용두역 4번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '7',
      'shared': '0',
      'stationId': 'ST-409',
      'stationLatitude': '37.570156',
      'stationLongitude': '127.048584',
      'stationName': '642. 신답역 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-410',
      'stationLatitude': '37.566971',
      'stationLongitude': '127.074417',
      'stationName': '643. 동대문구민체육센터 (육교아래)'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1298',
      'stationLatitude': '37.561867',
      'stationLongitude': '127.064377',
      'stationName': '646. 장한평역 1번출구 (국민은행앞)'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1299',
      'stationLatitude': '37.602798',
      'stationLongitude': '127.067268',
      'stationName': '647. 신이문역 1번출구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1300',
      'stationLatitude': '37.566700',
      'stationLongitude': '127.062424',
      'stationName': '648. 장안동위더스빌옆'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-1302',
      'stationLatitude': '37.591534',
      'stationLongitude': '127.067741',
      'stationName': '650. 중랑교사거리'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1303',
      'stationLatitude': '37.582748',
      'stationLongitude': '127.048279',
      'stationName': '651. 우리은행청량리지점앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-1447',
      'stationLatitude': '37.576530',
      'stationLongitude': '127.065941',
      'stationName': '652. 답십리 래미안엘파인아파트 입구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1449',
      'stationLatitude': '37.577621',
      'stationLongitude': '127.052109',
      'stationName': '654. 전농동 텃골공원'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1628',
      'stationLatitude': '37.587238',
      'stationLongitude': '127.043137',
      'stationName': '656. 영휘원 교차로'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '13',
      'shared': '77',
      'stationId': 'ST-1629',
      'stationLatitude': '37.575760',
      'stationLongitude': '127.048370',
      'stationName': '657. 동대문롯데캐슬아파트 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1630',
      'stationLatitude': '37.572948',
      'stationLongitude': '127.066147',
      'stationName': '658. 촬영소 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1631',
      'stationLatitude': '37.578350',
      'stationLongitude': '127.033386',
      'stationName': '659. 제기역1번출구'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1632',
      'stationLatitude': '37.577999',
      'stationLongitude': '127.037628',
      'stationName': '660. 동의보감타워'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1625',
      'stationLatitude': '37.594601',
      'stationLongitude': '127.051964',
      'stationName': '661. 경희대학교 청운관'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1671',
      'stationLatitude': '37.594891',
      'stationLongitude': '127.063026',
      'stationName': '663. 외대앞역 4번출구'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '20',
      'shared': '40',
      'stationId': 'ST-308',
      'stationLatitude': '37.546848',
      'stationLongitude': '126.872772',
      'stationName': '700. KB국민은행 염창역 지점 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-309',
      'stationLatitude': '37.532803',
      'stationLongitude': '126.863930',
      'stationName': '701. 목동사거리 부근'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '16',
      'shared': '25',
      'stationId': 'ST-310',
      'stationLatitude': '37.532543',
      'stationLongitude': '126.868729',
      'stationName': '702. 목4동주민센터 옆'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '12',
      'shared': '75',
      'stationId': 'ST-311',
      'stationLatitude': '37.524063',
      'stationLongitude': '126.875580',
      'stationName': '703. 오목교역 7번출구 앞'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-312',
      'stationLatitude': '37.523254',
      'stationLongitude': '126.864906',
      'stationName': '704. 남부법원검찰청 교차로'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-313',
      'stationLatitude': '37.521881',
      'stationLongitude': '126.851753',
      'stationName': '706. 신정네거리역'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-314',
      'stationLatitude': '37.515156',
      'stationLongitude': '126.854897',
      'stationName': '707. 신정3동주민센터'},
     {'parkingBikeTotCnt': '27',
      'rackTotCnt': '16',
      'shared': '169',
      'stationId': 'ST-315',
      'stationLatitude': '37.518970',
      'stationLongitude': '126.869965',
      'stationName': '708. 서울출입국관리사무소 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '20',
      'shared': '45',
      'stationId': 'ST-316',
      'stationLatitude': '37.511585',
      'stationLongitude': '126.841560',
      'stationName': '709. 신정3동 현장민원실 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '12',
      'shared': '133',
      'stationId': 'ST-317',
      'stationLatitude': '37.510658',
      'stationLongitude': '126.842537',
      'stationName': '710. 서부화물트럭터미널 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '20',
      'shared': '0',
      'stationId': 'ST-318',
      'stationLatitude': '37.517059',
      'stationLongitude': '126.848488',
      'stationName': '711. 신일해피트리아파트 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '14',
      'shared': '36',
      'stationId': 'ST-319',
      'stationLatitude': '37.516998',
      'stationLongitude': '126.838318',
      'stationName': '712. 강월초교입구 사거리'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '20',
      'shared': '15',
      'stationId': 'ST-320',
      'stationLatitude': '37.533047',
      'stationLongitude': '126.829956',
      'stationName': '713. 양서중학교 옆'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-321',
      'stationLatitude': '37.532547',
      'stationLongitude': '126.830803',
      'stationName': '714. 한국SGI 양천문화회관 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '15',
      'shared': '67',
      'stationId': 'ST-428',
      'stationLatitude': '37.517281',
      'stationLongitude': '126.864334',
      'stationName': '716.신정6동 주민센터 인근'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-431',
      'stationLatitude': '37.530369',
      'stationLongitude': '126.864258',
      'stationName': '719. 홍익병원앞 교차로'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-432',
      'stationLatitude': '37.516197',
      'stationLongitude': '126.834900',
      'stationName': '720. 서울강월초등학교 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-1000',
      'stationLatitude': '37.510380',
      'stationLongitude': '126.866798',
      'stationName': '729. 서부식자재마트 건너편'},
     {'parkingBikeTotCnt': '22',
      'rackTotCnt': '10',
      'shared': '220',
      'stationId': 'ST-1002',
      'stationLatitude': '37.529900',
      'stationLongitude': '126.876541',
      'stationName': '731. 서울시 도로환경관리센터'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1003',
      'stationLatitude': '37.539551',
      'stationLongitude': '126.828300',
      'stationName': '732. 신월동 이마트'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1004',
      'stationLatitude': '37.514099',
      'stationLongitude': '126.831001',
      'stationName': '733. 신정이펜하우스314동'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1005',
      'stationLatitude': '37.513950',
      'stationLongitude': '126.856056',
      'stationName': '734. 신트리공원 입구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1006',
      'stationLatitude': '37.536430',
      'stationLongitude': '126.871521',
      'stationName': '735. 영도초등학교'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1007',
      'stationLatitude': '37.522190',
      'stationLongitude': '126.836700',
      'stationName': '736. 오솔길공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1008',
      'stationLatitude': '37.522560',
      'stationLongitude': '126.849480',
      'stationName': '737. 장수공원'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '15',
      'shared': '27',
      'stationId': 'ST-1010',
      'stationLatitude': '37.536201',
      'stationLongitude': '126.827797',
      'stationName': '739. 신월사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1011',
      'stationLatitude': '37.536369',
      'stationLongitude': '126.831711',
      'stationName': '740. 으뜸공원'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1012',
      'stationLatitude': '37.539520',
      'stationLongitude': '126.825401',
      'stationName': '741. 화곡로 입구 교차로'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1013',
      'stationLatitude': '37.550732',
      'stationLongitude': '126.864578',
      'stationName': '742. 등촌역 5번 출구 뒤'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1014',
      'stationLatitude': '37.508900',
      'stationLongitude': '126.842682',
      'stationName': '743. 현대6차아파트 101동 옆'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '10',
      'shared': '170',
      'stationId': 'ST-1015',
      'stationLatitude': '37.543842',
      'stationLongitude': '126.882545',
      'stationName': '744. 신목동역 2번 출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1016',
      'stationLatitude': '37.522282',
      'stationLongitude': '126.839699',
      'stationName': '745. 강서초등학교'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1017',
      'stationLatitude': '37.536503',
      'stationLongitude': '126.877747',
      'stationName': '746. 목동2단지 상가'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1018',
      'stationLatitude': '37.534580',
      'stationLongitude': '126.875648',
      'stationName': '747. 목동3단지 상가'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1019',
      'stationLatitude': '37.530251',
      'stationLongitude': '126.879303',
      'stationName': '748. 목동운동장'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1350',
      'stationLatitude': '37.537228',
      'stationLongitude': '126.886612',
      'stationName': '749. 이대 목동병원 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1398',
      'stationLatitude': '37.512157',
      'stationLongitude': '126.835625',
      'stationName': '750. 연의근린공원 건너편'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1400',
      'stationLatitude': '37.542183',
      'stationLongitude': '126.863304',
      'stationName': '752. 성원2차 아파트'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1495',
      'stationLatitude': '37.541142',
      'stationLongitude': '126.876678',
      'stationName': '754. 목동1단지아파트 118동 앞 (월촌초등학교 정류소 옆)'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1496',
      'stationLatitude': '37.537868',
      'stationLongitude': '126.881409',
      'stationName': '755. 목동1단지아파트 상가 앞 (월촌중학교 버스정류소 옆)'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-1497',
      'stationLatitude': '37.526680',
      'stationLongitude': '126.876167',
      'stationName': '756. 목동주차장'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '10',
      'shared': '130',
      'stationId': 'ST-1498',
      'stationLatitude': '37.514278',
      'stationLongitude': '126.828743',
      'stationName': '757. 신정이펜하우스 1단지아파트 입구 사거리'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1499',
      'stationLatitude': '37.514721',
      'stationLongitude': '126.859200',
      'stationName': '758. 한사랑교회 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1500',
      'stationLatitude': '37.524071',
      'stationLongitude': '126.838600',
      'stationName': '759. 보아스아파트 앞'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1501',
      'stationLatitude': '37.506821',
      'stationLongitude': '126.844299',
      'stationName': '760. 잣절보도육교 아래'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1503',
      'stationLatitude': '37.524551',
      'stationLongitude': '126.877052',
      'stationName': '762. 오목로 무중력지대 앞'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1504',
      'stationLatitude': '37.510658',
      'stationLongitude': '126.859161',
      'stationName': '763. 목동11단지 아파트'},
     {'parkingBikeTotCnt': '20',
      'rackTotCnt': '30',
      'shared': '67',
      'stationId': 'ST-1505',
      'stationLatitude': '37.531029',
      'stationLongitude': '126.875893',
      'stationName': '764. 목동청소년수련관'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1731',
      'stationLatitude': '37.524776',
      'stationLongitude': '126.875481',
      'stationName': '765. 오목교역 3번출구'},
     {'parkingBikeTotCnt': '13',
      'rackTotCnt': '15',
      'shared': '87',
      'stationId': 'ST-1736',
      'stationLatitude': '37.544338',
      'stationLongitude': '126.883270',
      'stationName': '766. 신목동역 3번출구'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '15',
      'shared': '140',
      'stationId': 'ST-322',
      'stationLatitude': '37.532433',
      'stationLongitude': '126.954742',
      'stationName': '800. 목월공원 앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-324',
      'stationLatitude': '37.541153',
      'stationLongitude': '127.002213',
      'stationName': '802. 한강진역 2번 출구 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '10',
      'shared': '70',
      'stationId': 'ST-325',
      'stationLatitude': '37.538139',
      'stationLongitude': '127.004097',
      'stationName': '803. 한남초교 앞 보도육교'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '9',
      'shared': '133',
      'stationId': 'ST-326',
      'stationLatitude': '37.536758',
      'stationLongitude': '126.970001',
      'stationName': '805. 문배어린이공원 앞'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '20',
      'shared': '60',
      'stationId': 'ST-327',
      'stationLatitude': '37.533066',
      'stationLongitude': '126.960732',
      'stationName': '806. 전자랜드 본관 앞'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-328',
      'stationLatitude': '37.552277',
      'stationLongitude': '126.972687',
      'stationName': '807. 서울역 12번 출구 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-329',
      'stationLatitude': '37.520504',
      'stationLongitude': '126.989738',
      'stationName': '808. 서빙고동 금호맨션 앞'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-330',
      'stationLatitude': '37.530167',
      'stationLongitude': '127.007439',
      'stationName': '809. 한남 유수지 복개주차장'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-331',
      'stationLatitude': '37.538410',
      'stationLongitude': '126.986649',
      'stationName': '810. 이태원지하보도'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '20',
      'shared': '85',
      'stationId': 'ST-332',
      'stationLatitude': '37.535080',
      'stationLongitude': '126.985382',
      'stationName': '811. 녹사평역1번출구'},
     {'parkingBikeTotCnt': '18',
      'rackTotCnt': '20',
      'shared': '90',
      'stationId': 'ST-333',
      'stationLatitude': '37.534840',
      'stationLongitude': '126.977661',
      'stationName': '812. 용산전쟁기념관'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '20',
      'shared': '70',
      'stationId': 'ST-334',
      'stationLatitude': '37.533512',
      'stationLongitude': '126.972275',
      'stationName': '813. 삼각지역 3번출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '20',
      'shared': '10',
      'stationId': 'ST-335',
      'stationLatitude': '37.518509',
      'stationLongitude': '126.978798',
      'stationName': '815. LIG강촌아파트 103동앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-435',
      'stationLatitude': '37.530148',
      'stationLongitude': '126.968483',
      'stationName': '816. 신용산역 6번출구 앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '9',
      'shared': '22',
      'stationId': 'ST-436',
      'stationLatitude': '37.533451',
      'stationLongitude': '126.971733',
      'stationName': '817. 삼각지역 4번출구 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '15',
      'shared': '7',
      'stationId': 'ST-437',
      'stationLatitude': '37.544895',
      'stationLongitude': '126.969383',
      'stationName': '818. 숙명여대 입구 교차로'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '12',
      'shared': '42',
      'stationId': 'ST-438',
      'stationLatitude': '37.541653',
      'stationLongitude': '126.970505',
      'stationName': '819. 선린인터넷 고등학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-439',
      'stationLatitude': '37.549026',
      'stationLongitude': '126.971947',
      'stationName': '820. 청파동입구 교차로'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-440',
      'stationLatitude': '37.522041',
      'stationLongitude': '126.965523',
      'stationName': '822. 이촌1동 마을공원'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-441',
      'stationLatitude': '37.542320',
      'stationLongitude': '126.961960',
      'stationName': '823. 효창동주민센터 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '15',
      'shared': '33',
      'stationId': 'ST-442',
      'stationLatitude': '37.520336',
      'stationLongitude': '126.994263',
      'stationName': '825. 서빙고동 주민센터 앞'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '20',
      'shared': '25',
      'stationId': 'ST-1324',
      'stationLatitude': '37.541885',
      'stationLongitude': '126.979660',
      'stationName': '827. 국군복지단'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '7',
      'shared': '0',
      'stationId': 'ST-1325',
      'stationLatitude': '37.544079',
      'stationLongitude': '126.972000',
      'stationName': '828. 숙대입구역 8번'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '40',
      'shared': '43',
      'stationId': 'ST-1326',
      'stationLatitude': '37.522930',
      'stationLongitude': '126.961693',
      'stationName': '829. 베르가모앞'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1327',
      'stationLatitude': '37.534424',
      'stationLongitude': '126.948570',
      'stationName': '830. 청암자이아파트앞'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1328',
      'stationLatitude': '37.534279',
      'stationLongitude': '126.988564',
      'stationName': '831. 이태원관광특구입구'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1339',
      'stationLatitude': '37.521282',
      'stationLongitude': '126.973465',
      'stationName': '832. 이촌1동 주민센터 뒤'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1341',
      'stationLatitude': '37.539009',
      'stationLongitude': '126.961380',
      'stationName': '834. 효창공원앞역 3번출구 뒤'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1342',
      'stationLatitude': '37.541981',
      'stationLongitude': '126.971542',
      'stationName': '835. 남영역 건너편'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '15',
      'shared': '53',
      'stationId': 'ST-1343',
      'stationLatitude': '37.531422',
      'stationLongitude': '126.951500',
      'stationName': '836. 현대자동차서비스 앞'},
     {'parkingBikeTotCnt': '8',
      'rackTotCnt': '10',
      'shared': '80',
      'stationId': 'ST-1344',
      'stationLatitude': '37.529060',
      'stationLongitude': '127.006729',
      'stationName': '837. 한남나들목 입구'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '8',
      'shared': '13',
      'stationId': 'ST-1376',
      'stationLatitude': '37.544460',
      'stationLongitude': '126.972389',
      'stationName': '838. 숙대입구역 4번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-1441',
      'stationLatitude': '37.524010',
      'stationLongitude': '127.001450',
      'stationName': '839. 보광동 삼성리버빌아파트 앞'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1442',
      'stationLatitude': '37.523651',
      'stationLongitude': '126.970268',
      'stationName': '840. 용산 파크타워 앞'},
     {'parkingBikeTotCnt': '16',
      'rackTotCnt': '15',
      'shared': '107',
      'stationId': 'ST-1443',
      'stationLatitude': '37.529610',
      'stationLongitude': '126.968872',
      'stationName': '841. 신용산역 1번 출구'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1445',
      'stationLatitude': '37.533798',
      'stationLongitude': '126.988670',
      'stationName': '843. 녹사평역 광장'},
     {'parkingBikeTotCnt': '15',
      'rackTotCnt': '11',
      'shared': '136',
      'stationId': 'ST-1446',
      'stationLatitude': '37.527149',
      'stationLongitude': '126.955162',
      'stationName': '844. 이촌2동 동원베네스트 아파트 앞'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '22',
      'shared': '32',
      'stationId': 'ST-1615',
      'stationLatitude': '37.532700',
      'stationLongitude': '126.964378',
      'stationName': '845. 용산 선인상가'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1721',
      'stationLatitude': '37.546638',
      'stationLongitude': '126.981041',
      'stationName': '846. 용산중학교'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '20',
      'shared': '50',
      'stationId': 'ST-448',
      'stationLatitude': '37.603943',
      'stationLongitude': '126.927696',
      'stationName': '900. 은평예술회관'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-449',
      'stationLatitude': '37.600975',
      'stationLongitude': '126.926956',
      'stationName': '901. 응암1동사무소'},
     {'parkingBikeTotCnt': '10',
      'rackTotCnt': '10',
      'shared': '100',
      'stationId': 'ST-450',
      'stationLatitude': '37.643108',
      'stationLongitude': '126.918221',
      'stationName': '902. 진관동 은빛초등학교'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '20',
      'shared': '55',
      'stationId': 'ST-451',
      'stationLatitude': '37.645866',
      'stationLongitude': '126.927391',
      'stationName': '903. 은평뉴타운 아이파크'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '18',
      'shared': '78',
      'stationId': 'ST-452',
      'stationLatitude': '37.648674',
      'stationLongitude': '126.930702',
      'stationName': '904. 은평뉴타운 푸르지오'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '11',
      'shared': '127',
      'stationId': 'ST-453',
      'stationLatitude': '37.636234',
      'stationLongitude': '126.918999',
      'stationName': '905. 구파발역 2번출구'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '10',
      'shared': '60',
      'stationId': 'ST-454',
      'stationLatitude': '37.617210',
      'stationLongitude': '126.919579',
      'stationName': '906. 연신내역 5번출구150M 아래'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '10',
      'shared': '50',
      'stationId': 'ST-455',
      'stationLatitude': '37.599491',
      'stationLongitude': '126.916862',
      'stationName': '907. CJ 드림시티'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-456',
      'stationLatitude': '37.613186',
      'stationLongitude': '126.917351',
      'stationName': '908. 구산역 4번출구'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-457',
      'stationLatitude': '37.586994',
      'stationLongitude': '126.922882',
      'stationName': '909. 백련산 힐스테이트 3차'},
     {'parkingBikeTotCnt': '19',
      'rackTotCnt': '15',
      'shared': '127',
      'stationId': 'ST-1020',
      'stationLatitude': '37.597141',
      'stationLongitude': '126.909599',
      'stationName': '934. 신사동 성당'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '15',
      'shared': '93',
      'stationId': 'ST-1023',
      'stationLatitude': '37.645851',
      'stationLongitude': '126.923798',
      'stationName': '937. 상림마을 롯데캐슬2단지 옆'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '15',
      'shared': '73',
      'stationId': 'ST-1024',
      'stationLatitude': '37.644684',
      'stationLongitude': '126.918457',
      'stationName': '938. 금암 문화공원'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '15',
      'shared': '80',
      'stationId': 'ST-1025',
      'stationLatitude': '37.601700',
      'stationLongitude': '126.927422',
      'stationName': '939. 은평구청 교차로'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '13',
      'shared': '108',
      'stationId': 'ST-1027',
      'stationLatitude': '37.637222',
      'stationLongitude': '126.933304',
      'stationName': '941. 은평뉴타운 도서관'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '9',
      'shared': '78',
      'stationId': 'ST-1028',
      'stationLatitude': '37.644081',
      'stationLongitude': '126.929283',
      'stationName': '942. 상림마을 생태공원'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1029',
      'stationLatitude': '37.602402',
      'stationLongitude': '126.928650',
      'stationName': '943. 은평구청 보건소'},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '10',
      'shared': '30',
      'stationId': 'ST-1031',
      'stationLatitude': '37.634140',
      'stationLongitude': '126.932343',
      'stationName': '945. 기자촌 사거리'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1032',
      'stationLatitude': '37.618439',
      'stationLongitude': '126.932884',
      'stationName': '946. 독바위역 '},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1033',
      'stationLatitude': '37.622669',
      'stationLongitude': '126.919991',
      'stationName': '947. 연신내 선일하이츠빌 정류소'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '10',
      'shared': '40',
      'stationId': 'ST-1034',
      'stationLatitude': '37.577202',
      'stationLongitude': '126.902351',
      'stationName': '948. 디지털미디어 시티역 4번출구'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '7',
      'shared': '171',
      'stationId': 'ST-1035',
      'stationLatitude': '37.619781',
      'stationLongitude': '126.920807',
      'stationName': '949. 연신내역 1번 출구 '},
     {'parkingBikeTotCnt': '3',
      'rackTotCnt': '5',
      'shared': '60',
      'stationId': 'ST-1036',
      'stationLatitude': '37.610779',
      'stationLongitude': '126.917351',
      'stationName': '950. 구산역 2번 출구 '},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '15',
      'shared': '60',
      'stationId': 'ST-1037',
      'stationLatitude': '37.619305',
      'stationLongitude': '126.920593',
      'stationName': '951. 연신내역 6번출구옆'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1038',
      'stationLatitude': '37.622650',
      'stationLongitude': '126.925247',
      'stationName': '952. 서울연신중학교'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '10',
      'shared': '0',
      'stationId': 'ST-1039',
      'stationLatitude': '37.625778',
      'stationLongitude': '126.928818',
      'stationName': '953. 서울연신초등학교'},
     {'parkingBikeTotCnt': '11',
      'rackTotCnt': '10',
      'shared': '110',
      'stationId': 'ST-1329',
      'stationLatitude': '37.642609',
      'stationLongitude': '126.921478',
      'stationName': '954. 은평뉴타운구파발9단지'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '9',
      'shared': '67',
      'stationId': 'ST-1331',
      'stationLatitude': '37.594376',
      'stationLongitude': '126.918159',
      'stationName': '956. 응암시장교차로'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '13',
      'shared': '92',
      'stationId': 'ST-1479',
      'stationLatitude': '37.600361',
      'stationLongitude': '126.922813',
      'stationName': '958. 신한은행 응암동 지점 앞'},
     {'parkingBikeTotCnt': '14',
      'rackTotCnt': '10',
      'shared': '140',
      'stationId': 'ST-1480',
      'stationLatitude': '37.643661',
      'stationLongitude': '126.914558',
      'stationName': '959. 구파발10단지 인근'},
     {'parkingBikeTotCnt': '21',
      'rackTotCnt': '15',
      'shared': '140',
      'stationId': 'ST-1481',
      'stationLatitude': '37.638252',
      'stationLongitude': '126.919456',
      'stationName': '960. 구파발역 환승센터'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '8',
      'shared': '25',
      'stationId': 'ST-1482',
      'stationLatitude': '37.610970',
      'stationLongitude': '126.929810',
      'stationName': '961. 불광역 9번 출구'},
     {'parkingBikeTotCnt': '2',
      'rackTotCnt': '10',
      'shared': '20',
      'stationId': 'ST-1483',
      'stationLatitude': '37.639259',
      'stationLongitude': '126.918907',
      'stationName': '962. 은평뉴타운 힐데스하임'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '13',
      'shared': '0',
      'stationId': 'ST-1484',
      'stationLatitude': '37.614429',
      'stationLongitude': '126.932579',
      'stationName': '963. 대호프라자아파트'},
     {'parkingBikeTotCnt': '9',
      'rackTotCnt': '10',
      'shared': '90',
      'stationId': 'ST-1485',
      'stationLatitude': '37.616112',
      'stationLongitude': '126.925041',
      'stationName': '964. 북한산힐스테이트 7차아파트'},
     {'parkingBikeTotCnt': '1',
      'rackTotCnt': '10',
      'shared': '10',
      'stationId': 'ST-1486',
      'stationLatitude': '37.593479',
      'stationLongitude': '126.923187',
      'stationName': '965. 서울특별시 은평병원'},
     {'parkingBikeTotCnt': '12',
      'rackTotCnt': '10',
      'shared': '120',
      'stationId': 'ST-1487',
      'stationLatitude': '37.609032',
      'stationLongitude': '126.934677',
      'stationName': '966. 서울혁신파크1'},
     {'parkingBikeTotCnt': '5',
      'rackTotCnt': '13',
      'shared': '38',
      'stationId': 'ST-1488',
      'stationLatitude': '37.608910',
      'stationLongitude': '126.932419',
      'stationName': '967. 서울혁신파크2'},
     {'parkingBikeTotCnt': '4',
      'rackTotCnt': '7',
      'shared': '57',
      'stationId': 'ST-1489',
      'stationLatitude': '37.642090',
      'stationLongitude': '126.929413',
      'stationName': '968. 은평뉴타운 상림마을 13단지'},
     {'parkingBikeTotCnt': '6',
      'rackTotCnt': '9',
      'shared': '67',
      'stationId': 'ST-1490',
      'stationLatitude': '37.643860',
      'stationLongitude': '126.931877',
      'stationName': '969. 은평 지웰테라스'},
     {'parkingBikeTotCnt': '17',
      'rackTotCnt': '10',
      'shared': '170',
      'stationId': 'ST-1674',
      'stationLatitude': '37.602329',
      'stationLongitude': '126.906548',
      'stationName': '971. 역촌 센트레빌 아파트'},
     {'parkingBikeTotCnt': '7',
      'rackTotCnt': '20',
      'shared': '35',
      'stationId': 'ST-1751',
      'stationLatitude': '37.582161',
      'stationLongitude': '126.894928',
      'stationName': '972. 수색역'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '15',
      'shared': '0',
      'stationId': 'ST-1750',
      'stationLatitude': '37.577908',
      'stationLongitude': '126.798042',
      'stationName': '9993. 개화정비'},
     {'parkingBikeTotCnt': '0',
      'rackTotCnt': '2',
      'shared': '0',
      'stationId': 'ST-1738',
      'stationLatitude': '0.000000',
      'stationLongitude': '0.000000',
      'stationName': '9996. 시설2'},
     ...]




```python
df = pd.DataFrame(result)
df['datetime'] = pd.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>parkingBikeTotCnt</th>
      <th>rackTotCnt</th>
      <th>shared</th>
      <th>stationId</th>
      <th>stationLatitude</th>
      <th>stationLongitude</th>
      <th>stationName</th>
      <th>datetime</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>5</td>
      <td>120</td>
      <td>ST-3</td>
      <td>37.549561</td>
      <td>126.905754</td>
      <td>101. (구)합정동 주민센터</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>20</td>
      <td>20</td>
      <td>ST-4</td>
      <td>37.555649</td>
      <td>126.910629</td>
      <td>102. 망원역 1번출구 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>2</th>
      <td>48</td>
      <td>15</td>
      <td>320</td>
      <td>ST-1040</td>
      <td>37.549999</td>
      <td>127.174690</td>
      <td>1023. 한국종합기술사옥 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>3</th>
      <td>35</td>
      <td>10</td>
      <td>350</td>
      <td>ST-1041</td>
      <td>37.529251</td>
      <td>127.123108</td>
      <td>1024.  강동구청 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>4</th>
      <td>16</td>
      <td>10</td>
      <td>160</td>
      <td>ST-1042</td>
      <td>37.546841</td>
      <td>127.172516</td>
      <td>1025. 상일초등학교</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>14</td>
      <td>43</td>
      <td>ST-1043</td>
      <td>37.546631</td>
      <td>127.155884</td>
      <td>1026. 대명초교 입구 교차로</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>20</td>
      <td>35</td>
      <td>ST-1044</td>
      <td>37.535999</td>
      <td>127.147697</td>
      <td>1027. 프라자 아파트 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>10</td>
      <td>10</td>
      <td>ST-1045</td>
      <td>37.533100</td>
      <td>127.122780</td>
      <td>1028. 포레스 주상복합 빌딩</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>ST-1046</td>
      <td>37.536541</td>
      <td>127.125397</td>
      <td>1029. 롯데 시네마</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>9</th>
      <td>12</td>
      <td>15</td>
      <td>80</td>
      <td>ST-1047</td>
      <td>37.527061</td>
      <td>127.122070</td>
      <td>1030. 미호 플랜트 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>10</th>
      <td>16</td>
      <td>15</td>
      <td>107</td>
      <td>ST-1048</td>
      <td>37.555851</td>
      <td>127.129898</td>
      <td>1031. 암사동 CBIS</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>11</th>
      <td>10</td>
      <td>20</td>
      <td>50</td>
      <td>ST-1049</td>
      <td>37.556728</td>
      <td>127.136208</td>
      <td>1032. 선사고등학교</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>12</th>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>ST-1050</td>
      <td>37.557991</td>
      <td>127.144707</td>
      <td>1033. 고덕동 아남아파트</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>15</td>
      <td>0</td>
      <td>ST-1051</td>
      <td>37.561909</td>
      <td>127.150749</td>
      <td>1034. 고덕동 래미안 힐스테이트</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0</td>
      <td>20</td>
      <td>0</td>
      <td>ST-1052</td>
      <td>37.555016</td>
      <td>127.155273</td>
      <td>1035. 고덕역 4번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1</td>
      <td>10</td>
      <td>10</td>
      <td>ST-1053</td>
      <td>37.551998</td>
      <td>127.153297</td>
      <td>1036. 고덕동 주양쇼핑</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>16</th>
      <td>11</td>
      <td>10</td>
      <td>110</td>
      <td>ST-1054</td>
      <td>37.562588</td>
      <td>127.177612</td>
      <td>1037. 강일 6단지</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>17</th>
      <td>9</td>
      <td>10</td>
      <td>90</td>
      <td>ST-1055</td>
      <td>37.568668</td>
      <td>127.174797</td>
      <td>1038. 강일 다솜 어린이 공원</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>18</th>
      <td>14</td>
      <td>7</td>
      <td>200</td>
      <td>ST-1056</td>
      <td>37.561279</td>
      <td>127.167801</td>
      <td>1039. 고덕초등학교</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>19</th>
      <td>4</td>
      <td>10</td>
      <td>40</td>
      <td>ST-1058</td>
      <td>37.559196</td>
      <td>127.153297</td>
      <td>1041. 묘곡초등학교</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>20</th>
      <td>15</td>
      <td>10</td>
      <td>150</td>
      <td>ST-1059</td>
      <td>37.568562</td>
      <td>127.177002</td>
      <td>1042. 강일 2.5단지 사이</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>21</th>
      <td>19</td>
      <td>15</td>
      <td>127</td>
      <td>ST-1061</td>
      <td>37.545399</td>
      <td>127.142601</td>
      <td>1044. 굽은다리역</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>22</th>
      <td>5</td>
      <td>10</td>
      <td>50</td>
      <td>ST-1369</td>
      <td>37.536381</td>
      <td>127.137253</td>
      <td>1047. 건강보험 강동지사kt</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>23</th>
      <td>11</td>
      <td>10</td>
      <td>110</td>
      <td>ST-1370</td>
      <td>37.531013</td>
      <td>127.142365</td>
      <td>1048. 동부기업(둔촌동)</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>24</th>
      <td>6</td>
      <td>10</td>
      <td>60</td>
      <td>ST-1371</td>
      <td>37.561180</td>
      <td>127.180267</td>
      <td>1049. 강일동 10단지 아파트</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>25</th>
      <td>19</td>
      <td>15</td>
      <td>127</td>
      <td>ST-1420</td>
      <td>37.526695</td>
      <td>127.135529</td>
      <td>1050.  둔촌역 3번 출입구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1</td>
      <td>15</td>
      <td>7</td>
      <td>ST-1421</td>
      <td>37.554829</td>
      <td>127.137321</td>
      <td>1051. 양지시장 (용성약국앞) 입구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>27</th>
      <td>2</td>
      <td>10</td>
      <td>20</td>
      <td>ST-1593</td>
      <td>37.556469</td>
      <td>127.156822</td>
      <td>1052. 리싸이클시티</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>28</th>
      <td>2</td>
      <td>8</td>
      <td>25</td>
      <td>ST-1594</td>
      <td>37.562538</td>
      <td>127.164528</td>
      <td>1053. 동명근린공원 진입로 (아리수로)</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>29</th>
      <td>15</td>
      <td>10</td>
      <td>150</td>
      <td>ST-1595</td>
      <td>37.560009</td>
      <td>127.169579</td>
      <td>1054. 말우물 어린이 공원</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1503</th>
      <td>1</td>
      <td>10</td>
      <td>10</td>
      <td>ST-993</td>
      <td>37.521435</td>
      <td>126.857384</td>
      <td>722. LG전자베스트샵 신정점</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1504</th>
      <td>43</td>
      <td>15</td>
      <td>287</td>
      <td>ST-994</td>
      <td>37.529163</td>
      <td>126.872749</td>
      <td>723. SBS방송국</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1505</th>
      <td>5</td>
      <td>15</td>
      <td>33</td>
      <td>ST-995</td>
      <td>37.510681</td>
      <td>126.857399</td>
      <td>724. 계남공원 입구 주출입구 좌측</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1506</th>
      <td>1</td>
      <td>15</td>
      <td>7</td>
      <td>ST-996</td>
      <td>37.524334</td>
      <td>126.850548</td>
      <td>725. 양강중학교앞 교차로</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1507</th>
      <td>1</td>
      <td>15</td>
      <td>7</td>
      <td>ST-997</td>
      <td>37.534389</td>
      <td>126.869598</td>
      <td>726. 목동3단지 시내버스정류장</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1508</th>
      <td>0</td>
      <td>20</td>
      <td>0</td>
      <td>ST-946</td>
      <td>37.555367</td>
      <td>126.968643</td>
      <td>826. 서울역 서부교차로2</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1509</th>
      <td>3</td>
      <td>10</td>
      <td>30</td>
      <td>ST-459</td>
      <td>37.605583</td>
      <td>126.922935</td>
      <td>911. 은평평화공원(역촌역4번출구)</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1510</th>
      <td>9</td>
      <td>10</td>
      <td>90</td>
      <td>ST-460</td>
      <td>37.589661</td>
      <td>126.916946</td>
      <td>912. 응암오거리</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1511</th>
      <td>10</td>
      <td>15</td>
      <td>67</td>
      <td>ST-461</td>
      <td>37.600700</td>
      <td>126.920128</td>
      <td>913. 이마트 은평점</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1512</th>
      <td>23</td>
      <td>20</td>
      <td>115</td>
      <td>ST-462</td>
      <td>37.590797</td>
      <td>126.913651</td>
      <td>914. 새절역 2번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1513</th>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>ST-463</td>
      <td>37.584381</td>
      <td>126.909897</td>
      <td>915. 증산역 4번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1514</th>
      <td>0</td>
      <td>7</td>
      <td>0</td>
      <td>ST-464</td>
      <td>37.607849</td>
      <td>126.921326</td>
      <td>916. 평생학습관 앞</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1515</th>
      <td>9</td>
      <td>9</td>
      <td>100</td>
      <td>ST-465</td>
      <td>37.601299</td>
      <td>126.935349</td>
      <td>917. 녹번역 4번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1516</th>
      <td>9</td>
      <td>10</td>
      <td>90</td>
      <td>ST-467</td>
      <td>37.607025</td>
      <td>126.933311</td>
      <td>919. 서울혁신파크</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1517</th>
      <td>4</td>
      <td>10</td>
      <td>40</td>
      <td>ST-469</td>
      <td>37.630016</td>
      <td>126.919029</td>
      <td>921. 신도고등학교</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1518</th>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>ST-470</td>
      <td>37.617802</td>
      <td>126.921967</td>
      <td>922. 연신내역 4번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1519</th>
      <td>5</td>
      <td>10</td>
      <td>50</td>
      <td>ST-471</td>
      <td>37.620949</td>
      <td>126.925636</td>
      <td>923. 국민은행 연서지점</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1520</th>
      <td>1</td>
      <td>15</td>
      <td>7</td>
      <td>ST-472</td>
      <td>37.628517</td>
      <td>126.929581</td>
      <td>924. 메뚜기다리</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1521</th>
      <td>5</td>
      <td>8</td>
      <td>63</td>
      <td>ST-473</td>
      <td>37.609566</td>
      <td>126.930977</td>
      <td>925. 불광역 2번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1522</th>
      <td>5</td>
      <td>8</td>
      <td>63</td>
      <td>ST-474</td>
      <td>37.611179</td>
      <td>126.929665</td>
      <td>926. 불광역 8번출구</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1523</th>
      <td>4</td>
      <td>10</td>
      <td>40</td>
      <td>ST-475</td>
      <td>37.617855</td>
      <td>126.922523</td>
      <td>927. 연신내역 3번출구 인근</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1524</th>
      <td>14</td>
      <td>15</td>
      <td>93</td>
      <td>ST-476</td>
      <td>37.641315</td>
      <td>126.938042</td>
      <td>928. 은평역사한옥박물관</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1525</th>
      <td>3</td>
      <td>7</td>
      <td>43</td>
      <td>ST-478</td>
      <td>37.601662</td>
      <td>126.920303</td>
      <td>930. 구 서부경찰서 건너편</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1526</th>
      <td>6</td>
      <td>10</td>
      <td>60</td>
      <td>ST-479</td>
      <td>37.604736</td>
      <td>126.915337</td>
      <td>931. 역촌파출소</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1527</th>
      <td>10</td>
      <td>10</td>
      <td>100</td>
      <td>ST-480</td>
      <td>37.610004</td>
      <td>126.916397</td>
      <td>932. 예일여중</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1528</th>
      <td>7</td>
      <td>10</td>
      <td>70</td>
      <td>ST-481</td>
      <td>37.612484</td>
      <td>126.914879</td>
      <td>933. LG서비스 역촌점</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1529</th>
      <td>19</td>
      <td>20</td>
      <td>95</td>
      <td>ST-618</td>
      <td>37.483749</td>
      <td>126.982262</td>
      <td>9997.강남센터</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1530</th>
      <td>20</td>
      <td>14</td>
      <td>143</td>
      <td>ST-484</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>위트콤</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1531</th>
      <td>0</td>
      <td>66</td>
      <td>0</td>
      <td>ST-598</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>위트콤공장</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
    <tr>
      <th>1532</th>
      <td>14</td>
      <td>26</td>
      <td>54</td>
      <td>ST-48</td>
      <td>37.557598</td>
      <td>127.065308</td>
      <td>중랑센터</td>
      <td>2019-07-16 09:35:41</td>
    </tr>
  </tbody>
</table>
<p>1533 rows × 8 columns</p>
</div>




```python
df.to_csv('./realtime_bike_station_status.csv',encoding='utf8')
```


```python
df1 = pd.read_csv('./realtime_bike_station_status.csv',encoding='utf8')
```


```python
df1 = pd.read_csv('/Users/kim-youngjae/Downloads/seoul_bike_2015.csv',encoding='euc-kr')
```


```python
grp_bike = df1.groupby('자전거번호').sum()
grp_bike['이용횟수'] = df1.groupby('자전거번호').size()
grp_bike.sort_values("이용거리(M)",ascending=False)[['이용시간(분)', '이용거리(M)', '이용횟수']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이용시간(분)</th>
      <th>이용거리(M)</th>
      <th>이용횟수</th>
    </tr>
    <tr>
      <th>자전거번호</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>SPB-00297</th>
      <td>6164</td>
      <td>708150</td>
      <td>176</td>
    </tr>
    <tr>
      <th>SPB-00313</th>
      <td>4905</td>
      <td>647370</td>
      <td>178</td>
    </tr>
    <tr>
      <th>SPB-00071</th>
      <td>5674</td>
      <td>633430</td>
      <td>175</td>
    </tr>
    <tr>
      <th>SPB-00018</th>
      <td>5411</td>
      <td>605220</td>
      <td>169</td>
    </tr>
    <tr>
      <th>SPB-00400</th>
      <td>5248</td>
      <td>602200</td>
      <td>149</td>
    </tr>
    <tr>
      <th>SPB-00092</th>
      <td>4902</td>
      <td>596910</td>
      <td>150</td>
    </tr>
    <tr>
      <th>SPB-00530</th>
      <td>5284</td>
      <td>589800</td>
      <td>177</td>
    </tr>
    <tr>
      <th>SPB-00148</th>
      <td>4514</td>
      <td>587920</td>
      <td>156</td>
    </tr>
    <tr>
      <th>SPB-00244</th>
      <td>6477</td>
      <td>584670</td>
      <td>173</td>
    </tr>
    <tr>
      <th>SPB-00081</th>
      <td>4889</td>
      <td>583850</td>
      <td>154</td>
    </tr>
    <tr>
      <th>SPB-00463</th>
      <td>4750</td>
      <td>582020</td>
      <td>176</td>
    </tr>
    <tr>
      <th>SPB-00076</th>
      <td>5086</td>
      <td>570000</td>
      <td>196</td>
    </tr>
    <tr>
      <th>SPB-00470</th>
      <td>4693</td>
      <td>570000</td>
      <td>165</td>
    </tr>
    <tr>
      <th>SPB-00367</th>
      <td>5272</td>
      <td>566450</td>
      <td>148</td>
    </tr>
    <tr>
      <th>SPB-00129</th>
      <td>4850</td>
      <td>565490</td>
      <td>133</td>
    </tr>
    <tr>
      <th>SPB-00584</th>
      <td>5235</td>
      <td>563000</td>
      <td>164</td>
    </tr>
    <tr>
      <th>SPB-00562</th>
      <td>4354</td>
      <td>556180</td>
      <td>140</td>
    </tr>
    <tr>
      <th>SPB-00529</th>
      <td>5008</td>
      <td>554250</td>
      <td>184</td>
    </tr>
    <tr>
      <th>SPB-00384</th>
      <td>4860</td>
      <td>554000</td>
      <td>151</td>
    </tr>
    <tr>
      <th>SPB-00319</th>
      <td>4133</td>
      <td>553060</td>
      <td>161</td>
    </tr>
    <tr>
      <th>SPB-00404</th>
      <td>5000</td>
      <td>550050</td>
      <td>138</td>
    </tr>
    <tr>
      <th>SPB-00217</th>
      <td>4896</td>
      <td>548690</td>
      <td>174</td>
    </tr>
    <tr>
      <th>SPB-00126</th>
      <td>4521</td>
      <td>546550</td>
      <td>139</td>
    </tr>
    <tr>
      <th>SPB-00186</th>
      <td>4570</td>
      <td>546210</td>
      <td>162</td>
    </tr>
    <tr>
      <th>SPB-00034</th>
      <td>4886</td>
      <td>542280</td>
      <td>164</td>
    </tr>
    <tr>
      <th>SPB-00012</th>
      <td>4597</td>
      <td>539020</td>
      <td>157</td>
    </tr>
    <tr>
      <th>SPB-00347</th>
      <td>4078</td>
      <td>539010</td>
      <td>150</td>
    </tr>
    <tr>
      <th>SPB-00482</th>
      <td>4177</td>
      <td>538380</td>
      <td>150</td>
    </tr>
    <tr>
      <th>SPB-00414</th>
      <td>4553</td>
      <td>538090</td>
      <td>143</td>
    </tr>
    <tr>
      <th>SPB-00438</th>
      <td>5080</td>
      <td>537570</td>
      <td>156</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>SPB-00070</th>
      <td>4586</td>
      <td>13870</td>
      <td>138</td>
    </tr>
    <tr>
      <th>SPB-01317</th>
      <td>178</td>
      <td>13030</td>
      <td>7</td>
    </tr>
    <tr>
      <th>SPB-01367</th>
      <td>77</td>
      <td>12500</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SPB-01081</th>
      <td>182</td>
      <td>12170</td>
      <td>8</td>
    </tr>
    <tr>
      <th>SPB-00332</th>
      <td>357</td>
      <td>10370</td>
      <td>6</td>
    </tr>
    <tr>
      <th>SPB-01358</th>
      <td>108</td>
      <td>10210</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SPB-01342</th>
      <td>829</td>
      <td>9100</td>
      <td>49</td>
    </tr>
    <tr>
      <th>SPB-01269</th>
      <td>97</td>
      <td>7850</td>
      <td>2</td>
    </tr>
    <tr>
      <th>SPB-01213</th>
      <td>77</td>
      <td>6820</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-01284</th>
      <td>35</td>
      <td>6570</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SPB-01043</th>
      <td>48</td>
      <td>6420</td>
      <td>2</td>
    </tr>
    <tr>
      <th>SPB-01224</th>
      <td>50</td>
      <td>6020</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SPB-01308</th>
      <td>38</td>
      <td>4870</td>
      <td>4</td>
    </tr>
    <tr>
      <th>SPB-01357</th>
      <td>30</td>
      <td>4720</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00459</th>
      <td>116</td>
      <td>3940</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SPB-01293</th>
      <td>17</td>
      <td>2980</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00204</th>
      <td>4312</td>
      <td>2420</td>
      <td>119</td>
    </tr>
    <tr>
      <th>SPB-00942</th>
      <td>6</td>
      <td>1280</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00224</th>
      <td>9</td>
      <td>850</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00653</th>
      <td>12</td>
      <td>550</td>
      <td>2</td>
    </tr>
    <tr>
      <th>SPB-00856</th>
      <td>32</td>
      <td>130</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00831</th>
      <td>13</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00509</th>
      <td>10</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>SPB-00195</th>
      <td>1506</td>
      <td>0</td>
      <td>36</td>
    </tr>
    <tr>
      <th>SPB-00666</th>
      <td>2</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-01117</th>
      <td>1117</td>
      <td>0</td>
      <td>39</td>
    </tr>
    <tr>
      <th>SPB-01264</th>
      <td>2</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-01278</th>
      <td>2</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00075</th>
      <td>55</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>SPB-00190</th>
      <td>6</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>1265 rows × 3 columns</p>
</div>




```python
df1.groupby('자전거번호').size()
```




    자전거번호
    SPB-00001    110
    SPB-00002     90
    SPB-00003    122
    SPB-00004    147
    SPB-00005    110
    SPB-00006    155
    SPB-00007    119
    SPB-00008    110
    SPB-00009     51
    SPB-00010     61
    SPB-00011     39
    SPB-00012    157
    SPB-00013     41
    SPB-00015    180
    SPB-00016     90
    SPB-00017     31
    SPB-00018    169
    SPB-00019    104
    SPB-00020     73
    SPB-00021     99
    SPB-00022     83
    SPB-00023     83
    SPB-00024    181
    SPB-00025    102
    SPB-00026     53
    SPB-00027    126
    SPB-00028    102
    SPB-00029     90
    SPB-00030    110
    SPB-00031    154
                ... 
    SPB-01334      5
    SPB-01335     59
    SPB-01336      9
    SPB-01337     65
    SPB-01338     35
    SPB-01342     49
    SPB-01343     53
    SPB-01344     42
    SPB-01345     47
    SPB-01346     50
    SPB-01347     31
    SPB-01348     34
    SPB-01349     37
    SPB-01351     18
    SPB-01353     32
    SPB-01354     68
    SPB-01355     49
    SPB-01356     92
    SPB-01357      1
    SPB-01358      3
    SPB-01359     52
    SPB-01360     46
    SPB-01361     51
    SPB-01363     56
    SPB-01364      8
    SPB-01365     17
    SPB-01367      3
    SPB-01368     44
    SPB-01369     77
    SPB-01371     10
    Length: 1265, dtype: int64




```python
from pandas.io.json import json_normalize
import json

with open('/Users/kim-youngjae/Kim/2.Study/2.TCL/2019/dt-tcl/data/서울시 자전거 편의시설 정보.json') as data_file:    
    d= json.load(data_file)  

df = json_normalize(d, 'DATA')
df.iloc[0:50]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>addr_dong</th>
      <th>addr_gu</th>
      <th>addr_num1</th>
      <th>addr_num2</th>
      <th>content_id</th>
      <th>content_nm</th>
      <th>coordinate_x</th>
      <th>coordinate_y</th>
      <th>detail_content1</th>
      <th>detail_content2</th>
      <th>...</th>
      <th>detail_title7</th>
      <th>detail_title8</th>
      <th>detail_title9</th>
      <th>national_area</th>
      <th>new_addr</th>
      <th>space_object_type</th>
      <th>subcategory_nm</th>
      <th>tel_number</th>
      <th>use_yn</th>
      <th>web_url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>None</td>
      <td>강남구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000077</td>
      <td>7호선 청담역13번출구</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>수동식</td>
      <td>None</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>역삼동</td>
      <td>강남구</td>
      <td>858-26</td>
      <td>None</td>
      <td>AR000078</td>
      <td>9호선 신논현역(5번 출구)</td>
      <td>127.024950</td>
      <td>37.504180</td>
      <td>수동식</td>
      <td>5번 출구 뒤편</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06123</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>2</th>
      <td>논현동</td>
      <td>강남구</td>
      <td>87-8</td>
      <td>None</td>
      <td>AR000079</td>
      <td>7호선 학동역(8,10번 출구)</td>
      <td>127.030844</td>
      <td>37.514267</td>
      <td>수동식</td>
      <td>8번, 10번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06052</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>3</th>
      <td>도곡동</td>
      <td>강남구</td>
      <td>467-5</td>
      <td>None</td>
      <td>AR000080</td>
      <td>3호선 도곡역(4번 출구)</td>
      <td>127.055030</td>
      <td>37.490554</td>
      <td>수동식</td>
      <td>4번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06293</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>4</th>
      <td>도곡동</td>
      <td>강남구</td>
      <td>179-7</td>
      <td>None</td>
      <td>AR000081</td>
      <td>3호선 매봉역(4번 출구)</td>
      <td>127.046096</td>
      <td>37.486464</td>
      <td>수동식</td>
      <td>4번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06297</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>5</th>
      <td>개포동</td>
      <td>강남구</td>
      <td>186-20</td>
      <td>None</td>
      <td>AR000082</td>
      <td>분당선 개포동역(4번 출구)</td>
      <td>127.066349</td>
      <td>37.489266</td>
      <td>수동식</td>
      <td>4번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06324</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>6</th>
      <td>None</td>
      <td>강남구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000083</td>
      <td>7호선 학동역 10번출구 앞</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>수동식</td>
      <td>10번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>7</th>
      <td>구로동</td>
      <td>구로구</td>
      <td>810-3</td>
      <td>None</td>
      <td>AR000084</td>
      <td>2호선 구로디지털단지역</td>
      <td>126.901445</td>
      <td>37.485249</td>
      <td>수동식</td>
      <td>구로디지털단지역</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08391</td>
      <td>도림천로 477</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>8</th>
      <td>문정동</td>
      <td>송파구</td>
      <td>227-1</td>
      <td>None</td>
      <td>AR000085</td>
      <td>8호선 문정역(1,2번 출구)</td>
      <td>127.122515</td>
      <td>37.486428</td>
      <td>자동식</td>
      <td>1,2번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>05806</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>9</th>
      <td>신천동</td>
      <td>송파구</td>
      <td>17-9</td>
      <td>None</td>
      <td>AR000086</td>
      <td>2호선 잠실나루역(1번 출구)</td>
      <td>127.103884</td>
      <td>37.520966</td>
      <td>자동식</td>
      <td>1번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>05504</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>10</th>
      <td>가락동</td>
      <td>송파구</td>
      <td>123-27</td>
      <td>None</td>
      <td>AR000087</td>
      <td>3.5호선 경찰병원역(4번 출구)</td>
      <td>127.123833</td>
      <td>37.495092</td>
      <td>자동식</td>
      <td>4번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>05828</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>11</th>
      <td>잠원동</td>
      <td>서초구</td>
      <td>61-7</td>
      <td>None</td>
      <td>AR000088</td>
      <td>잠원역(3번 출구)</td>
      <td>127.011124</td>
      <td>37.512839</td>
      <td>자동식</td>
      <td>3번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06522</td>
      <td>잠원로4길 46</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>12</th>
      <td>양재동</td>
      <td>서초구</td>
      <td>237-2</td>
      <td>None</td>
      <td>AR000089</td>
      <td>양재시민의숲역(1번 출구)</td>
      <td>127.038576</td>
      <td>37.470354</td>
      <td>자동식</td>
      <td>1번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06774</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>13</th>
      <td>상계동</td>
      <td>노원구</td>
      <td>65-47</td>
      <td>None</td>
      <td>AR000090</td>
      <td>자전거대여소(당고개역)</td>
      <td>127.078765</td>
      <td>37.669978</td>
      <td>자동식</td>
      <td>상계동 111번지</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>01637</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>14</th>
      <td>중계동</td>
      <td>노원구</td>
      <td>141-87</td>
      <td>None</td>
      <td>AR000091</td>
      <td>자전거대여소(상계역)</td>
      <td>127.073934</td>
      <td>37.661201</td>
      <td>자동식</td>
      <td>상계동 173</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>01663</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>15</th>
      <td>봉천동</td>
      <td>관악구</td>
      <td>926-33</td>
      <td>None</td>
      <td>AR000092</td>
      <td>봉천역(6번출구)</td>
      <td>126.942652</td>
      <td>37.482483</td>
      <td>자동식</td>
      <td>6번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08757</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>16</th>
      <td>남현동</td>
      <td>관악구</td>
      <td>1130-1</td>
      <td>None</td>
      <td>AR000093</td>
      <td>사당역(6번 출구)</td>
      <td>126.980880</td>
      <td>37.476363</td>
      <td>자동식</td>
      <td>6번 출구 뒤</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08806</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>17</th>
      <td>신림동</td>
      <td>관악구</td>
      <td>516</td>
      <td>None</td>
      <td>AR000094</td>
      <td>신대방역(1,2번 출구)</td>
      <td>126.913377</td>
      <td>37.487200</td>
      <td>자동식</td>
      <td>1,2번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08702</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>18</th>
      <td>신림동</td>
      <td>관악구</td>
      <td>1422-42</td>
      <td>None</td>
      <td>AR000095</td>
      <td>신림역(2,8번 출구)</td>
      <td>126.930102</td>
      <td>37.484489</td>
      <td>자동식</td>
      <td>2,8번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08754</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>19</th>
      <td>None</td>
      <td>관악구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000096</td>
      <td>서울대입구역(8번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>8번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>20</th>
      <td>None</td>
      <td>관악구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000097</td>
      <td>신림역(2번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>2번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>21</th>
      <td>None</td>
      <td>관악구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000098</td>
      <td>신대방역(2번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>2번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>22</th>
      <td>None</td>
      <td>관악구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000099</td>
      <td>신대방역(1번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>1번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>23</th>
      <td>None</td>
      <td>관악구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000100</td>
      <td>신대방역(1번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>1번 출구 앞</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>24</th>
      <td>None</td>
      <td>마포구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000101</td>
      <td>수색역(3번 출구)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>3번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>25</th>
      <td>망원동</td>
      <td>마포구</td>
      <td>472-1</td>
      <td>None</td>
      <td>AR000102</td>
      <td>마포구청역(6번 출구)</td>
      <td>126.903603</td>
      <td>37.562690</td>
      <td>자동식</td>
      <td>6번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03962</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>26</th>
      <td>서교동</td>
      <td>마포구</td>
      <td>441-19</td>
      <td>None</td>
      <td>AR000103</td>
      <td>망원역(1번 출구)</td>
      <td>126.910382</td>
      <td>37.556012</td>
      <td>자동식</td>
      <td>1번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03996</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>27</th>
      <td>합정동</td>
      <td>마포구</td>
      <td>373-26</td>
      <td>None</td>
      <td>AR000104</td>
      <td>합정역(7번 출구)</td>
      <td>126.913741</td>
      <td>37.548734</td>
      <td>자동식</td>
      <td>7번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>04071</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>28</th>
      <td>동교동</td>
      <td>마포구</td>
      <td>192-44</td>
      <td>None</td>
      <td>AR000105</td>
      <td>홍대입구역(KT옆)</td>
      <td>126.923560</td>
      <td>37.557751</td>
      <td>자동식</td>
      <td>홍대입구역 KT옆</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03994</td>
      <td>월드컵북로2길 65</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>29</th>
      <td>녹번동</td>
      <td>은평구</td>
      <td>49-3</td>
      <td>None</td>
      <td>AR000106</td>
      <td>녹번역(5번 출구)</td>
      <td>126.935334</td>
      <td>37.601347</td>
      <td>자동식</td>
      <td>5번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03382</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>30</th>
      <td>증산동</td>
      <td>은평구</td>
      <td>198-2</td>
      <td>None</td>
      <td>AR000107</td>
      <td>증산역(4번 출구)</td>
      <td>126.910114</td>
      <td>37.584507</td>
      <td>자동식</td>
      <td>4번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03499</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>31</th>
      <td>갈현동</td>
      <td>은평구</td>
      <td>530-20</td>
      <td>None</td>
      <td>AR000108</td>
      <td>구산역(4번 출구)</td>
      <td>126.917177</td>
      <td>37.611663</td>
      <td>자동식</td>
      <td>4번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03336</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>32</th>
      <td>역촌동</td>
      <td>은평구</td>
      <td>17-1</td>
      <td>None</td>
      <td>AR000109</td>
      <td>역촌역(1번 출구)</td>
      <td>126.922525</td>
      <td>37.606053</td>
      <td>자동식</td>
      <td>1번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03404</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>33</th>
      <td>불광동</td>
      <td>은평구</td>
      <td>13-33</td>
      <td>None</td>
      <td>AR000110</td>
      <td>독바위역(1번 출구)</td>
      <td>126.932846</td>
      <td>37.618393</td>
      <td>자동식</td>
      <td>1번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03354</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>34</th>
      <td>진관동</td>
      <td>은평구</td>
      <td>221-29</td>
      <td>None</td>
      <td>AR000111</td>
      <td>구파발역(2번 출구)</td>
      <td>126.919232</td>
      <td>37.636196</td>
      <td>자동식</td>
      <td>2번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03306</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>35</th>
      <td>대조동</td>
      <td>은평구</td>
      <td>227-1</td>
      <td>None</td>
      <td>AR000112</td>
      <td>연신내역(4~5번출구)</td>
      <td>126.921269</td>
      <td>37.618687</td>
      <td>자동식</td>
      <td>4~5번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03385</td>
      <td>통일로 843-2</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>36</th>
      <td>응암동</td>
      <td>은평구</td>
      <td>610-3</td>
      <td>None</td>
      <td>AR000113</td>
      <td>새절역(2번 출구)</td>
      <td>126.913813</td>
      <td>37.591254</td>
      <td>자동식</td>
      <td>2번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03442</td>
      <td>증산로 391</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>37</th>
      <td>응암동</td>
      <td>은평구</td>
      <td>91-15</td>
      <td>None</td>
      <td>AR000114</td>
      <td>응암역(3번 출구)</td>
      <td>126.916035</td>
      <td>37.599363</td>
      <td>자동식</td>
      <td>3번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03421</td>
      <td>연서로 5</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>38</th>
      <td>증산동</td>
      <td>은평구</td>
      <td>223-25</td>
      <td>None</td>
      <td>AR000115</td>
      <td>디지털미디어시티역(4번 출구)</td>
      <td>126.902179</td>
      <td>37.577497</td>
      <td>자동식</td>
      <td>4번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>03504</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>39</th>
      <td>None</td>
      <td>양천구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000116</td>
      <td>목동역(4번 출구)</td>
      <td>126.864658</td>
      <td>37.526375</td>
      <td>자동식</td>
      <td>4번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>07993</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>40</th>
      <td>목동</td>
      <td>양천구</td>
      <td>404-177</td>
      <td>None</td>
      <td>AR000117</td>
      <td>오목교역(5~6번 출구 사이)</td>
      <td>126.876254</td>
      <td>37.524141</td>
      <td>자동식</td>
      <td>5~6번 출구 사이</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08007</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>41</th>
      <td>일원동</td>
      <td>강남구</td>
      <td>700-10</td>
      <td>None</td>
      <td>AR000161</td>
      <td>대청역(3번출구 중동고 옆)</td>
      <td>127.080021</td>
      <td>37.493638</td>
      <td>자동식</td>
      <td>3번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>06338</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>42</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000162</td>
      <td>개봉역(남측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>개봉동 202-43</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>43</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000163</td>
      <td>개봉역(북측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>개봉동 417-7</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>44</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000164</td>
      <td>신도림역(남측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>구로동 3-55</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>45</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000165</td>
      <td>온수역(북측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>온수동 11-16</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>46</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000166</td>
      <td>오류동역(북측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>오류동 66-7</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>N</td>
      <td>None</td>
    </tr>
    <tr>
      <th>47</th>
      <td>None</td>
      <td>구로구</td>
      <td>None</td>
      <td>None</td>
      <td>AR000167</td>
      <td>구일역</td>
      <td>126.870921</td>
      <td>37.496078</td>
      <td>자동식</td>
      <td>구로동 642-76</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08323</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>48</th>
      <td>구로동</td>
      <td>구로구</td>
      <td>603</td>
      <td>31</td>
      <td>AR000168</td>
      <td>구로역(북측)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>자동식</td>
      <td>구로동 603-31</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
    <tr>
      <th>49</th>
      <td>구로동</td>
      <td>구로구</td>
      <td>125-53</td>
      <td>None</td>
      <td>AR000169</td>
      <td>대림역(1,2번 출구)</td>
      <td>126.894826</td>
      <td>37.492480</td>
      <td>자동식</td>
      <td>1,2번 출구</td>
      <td>...</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>08305</td>
      <td>None</td>
      <td>1</td>
      <td>공기주입기</td>
      <td>None</td>
      <td>Y</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
<p>50 rows × 33 columns</p>
</div>


