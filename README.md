https://hortonassets.s3.amazonaws.com/tutorial/hive/Twitterdata.txt

Dữliệubaogồmcáctrườngnhư:id,username,content,timestamp,location,retweet_count,vàfavorite_count.
SELECT username, 
       SUM(retweet_count) AS total_retweets, 
       SUM(favorite_count) AS total_favorites
FROM giao_dich
GROUP BY username;


SELECT username, SUM(retweet_count) AS total_retweets
FROM giao_dich
GROUP BY username
ORDER BY total_retweets DESC
LIMIT 1;

SELECT location, COUNT(*) AS total_tweets
FROM giao_dich
WHERE location IS NOT NULL
GROUP BY location
ORDER BY total_tweets DESC;

SELECT LEFT(timestamp, 10) AS ngay, COUNT(*) AS so_luong_tweet

ALTER TABLE giao_dich
ALTER COLUMN timestamp DATE;

FROM giao_dich
GROUP BY ngay;

SELECT DATE(timestamp) AS ngay, COUNT(*) AS so_luong_tweet
FROM giao_dich
GROUP BY ngay;
