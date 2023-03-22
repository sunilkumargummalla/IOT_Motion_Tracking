## MYSQL Database setup for Motion tracking 

```
create database motiondb;
use motiondb;
create table mpudata1 ( tstamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP, XAcc int, YAcc int, ZAcc int, XGyro int, YGyro int, ZGyro int, primary key(tstamp));
```
