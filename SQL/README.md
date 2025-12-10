📌 SQL Analysis – OTT Analytics Project

This folder contains all SQL work done for the OTT Analytics Project, including data exploration, data cleaning, transformations, and analytical queries used to generate insights.

Database Schema Overview :
The project uses four main tables:

Table Name	    Description
users         	Contains user information such as name and country
shows	          Contains show metadata like title and genre
subscriptions	  Stores subscription details including start dates and payment amounts
watch_history	  Tracks what each user watched, duration, and completion status

Key SQL Queries Executed✅
1. 📍Most Watched Genre:
select s.genre, sum(w.watch_duration_min) as total_watch_time
from shows s 
join watch_history w on s.show_id = w.show_id
group by s.genre 
order by total_watch_time desc;
(Insight: Romance is the most-watched genre with 260 minutes of watch-time.)

2.📍Top 3 Binge Watchers:
select u.name, sum(w.watch_duration_min) as total_watch_time
from users u
join watch_history w on u.user_id = w.user_id
group by u.name
order by total_watch_time desc
limit 3;
(Insight: Asha Kumar, Rahul Sen, and Tom Lee are the top binge users.)

3.📍Monthly Revenue Trend:
select date_format(start_date,'%y-%m') as month,
sum(amount_paid) as total_revenue
from subscriptions
group by month
order by total_revenue desc;
(Insight: Highest revenue was generated in January.)

4.📍Most Completed Show by Country:
select u.country, s.title, sum(w.completed) as completed_count
from users u
join watch_history w on u.user_id = w.user_id
join shows s on w.show_id = s.show_id
group by u.country, s.title
order by u.country, completed_count desc;
(Insight:
India → Love in Chennai
UK → Space Frontier & Animated Fun
USA → No show completed fully)

✅ Summary of Insights :

Romance is the most popular genre.

Asha Kumar leads binge-watching activity.

January generated the highest subscription revenue.

User preferences differ across countries.

Completion rate varies widely across shows.


📁 Files Included :

SQL screenshots
README documentation (this file)





