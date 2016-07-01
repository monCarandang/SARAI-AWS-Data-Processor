# SARAI-AWS-Data-Processor
Retrieves data from Weather Underground and stores it in the SARAI project's DB

The program connects to the mongodb (must be running) supplied in the parameters. It checks the dss-settings collection for the date when the weather data was last updated. Then it takes all the weather stations from the weather-stations collection and updates each of them one day at a time until yesterday's data is fetched.(Will not get today's data from weather underground).

The program fetches weather data from 10 stations in succession then sleeps for a minute. This is done because the free wunderground API key only allows 500 calls a day, and only 10 calls a minute.

https://www.wunderground.com/weather/api/


#Additional Notes
Typical output looks like this:
1: Updated IILOCOSR3 (20160627)
2: Updated ICAGAYAN2 (20160627)
3: Updated IILOCOSR4 (20160627)
4: Updated IBULACAN2 (20160627)
5: MISSING DATA ICORDILL2 (20160627)

'MISSING DATA' means that no data was returned by weahter underground.

#usage
java -jar SARAI-AWS-Data-Processor.jar &lt;host&gt; &lt;port&gt;

meteor mongo is usually in 127.0.0.1 3001
