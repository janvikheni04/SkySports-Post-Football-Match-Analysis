create database sp;
show databases;

use sp;

select * from overall_wc_stats;
select * from group_stage_team_stats;

#Write an sql query to show all the UNIQUE team names
select distinct(team) from group_stage_team_stats;

#Write an SQL query to show name of team which has rank 1 from group 7 
select team from group_stage_team_stats where 'group' = 7 and 'rank'=1;
select team from group_stage_team_stats  where `rank`=1 and `group`=7;

#Write an sql query to show count of all teams
select count(team) from group_stage_team_stats;

#Write an SQL query to show matches_played by each team
select  team, matches_played from group_stage_team_stats;

#Write an SQL query to show team, percent of wins with respect to matches_played by each team and name the resulting column as wins_percent
select team, 100.0*(wins/matches_played) as wins_percent from group_stage_team_stats gsts;

#Write an SQL query to show which team has maximum goals_scored and their count
select team, goals_scored from group_stage_team_stats where goals_scored = (select max(goals_scored) from group_stage_team_stats);

#Write an SQL query to show percent of draws with respect to matches_played round of to 2 digits by each team
select team, round(100.00*(draws/matches_played),2)  Draws_percentage from group_stage_team_stats;

#Write an SQL query to show which team has minimum goals_scored and their count
select team, min(goals_scored) from group_stage_team_stats;
select team, goals_scored from group_stage_team_stats where goals_scored = (select min(goals_scored) from group_stage_team_stats);

#Write an SQL query to show percent of losses with respect to matches_played by each team in ascending order by losses and name the resulting column as losses_percent
select team,  100.0*(losses/matches_played) as l_percent from group_stage_team_stats order by l_percent;

#Write an SQL query to show the average goal_difference
select team, avg(goal_difference) from group_stage_team_stats;

#Write an SQL query to show name of the team where points are 0
select team from group_stage_team_stats gsts where points ='0';

select * from  group_stage_team_stats;
#Write a SQL query to show all data where expected_goal_scored is less than exp_goal_conceded
select * from group_stage_team_stats where expected_goal_scored < exp_goal_conceded;

#Write an SQL query to show data where exp_goal_difference is in between -0.5 and 0.5
select * from group_stage_team_stats where exp_goal_difference between -0.5 and 0.5;

#Write an SQL query to show all data in ascending order by exp_goal_difference_per_90
select * from group_stage_team_stats where exp_goal_difference_per_90 order by exp_goal_difference_per_90;

#Write an SQL query to show team which has maximum number of players_used
select team, players_used from overall_wc_stats where players_used =(select max(players_used) from overall_wc_stats);

#Write an SQL query to show each team name and avg_age in ascending order by avg_age
select team, avg_age from overall_wc_stats order by avg_age;

#Write an sql query to show average possession of teams 
select avg(possession) from overall_wc_stats;


#Write a SQL query to show team which has played atleast 5 games
select team, games from overall_wc_stats where games >= 5;

#Write an SQL query to show all data for which minutes is greater than 600
select * from overall_wc_stats where minutes > 600;



#Write an SQL query to show team, goals, assists in ascending order by goals
select team, goals, assists  from overall_wc_stats order by goals;

#Write an SQL query to show team, pens_made, pens_att in descending order by pens_made
select team, pens_made, pens_att from overall_wc_stats order by pens_made desc;

#Write an SQL query to show team, cards_yellow, cards_red where cards_red is equal to 1 in ascending order by cards_yellow
select team, cards_yellow, cards_red from overall_wc_stats where cards_red =1 order by cards_yellow;

#Write an SQL query to show team, goals_per90, assists_per90, goals_assists_per90 in descending order by goals_assists_per90
select team, goals_per90, assists_per90, goals_assists_per90 from overall_wc_stats order by goals_assists_per90 desc;

#Write an SQL query to show team, goals_pens_per90, goals_assists_pens_per90 in ascending order by goals_assists_pens_per90
select team, goals_pens_per90, goals_assists_pens_per90 from overall_wc_stats order by goals_assists_pens_per90;

#Write an SQL query to show team, shots, shots_on_target, shots_on_target_pct where shots_on_target_pct is less than 30 in ascending order by shots_on_target_pct
select team, shots, shots_on_target, shots_on_target_pct from overall_wc_stats where shots_on_target_pct < 30 order by shots_on_target_pct;

#Write an SQL query to show team, shots_per90, shots_on_target_per90 for team Belgium
select team, shots_per90, shots_on_target_per90 from overall_wc_stats where team='Belgium';

#Write an SQL query to show team, goals_per_shot, goals_per_shot_on_target, average_shot_distance in descending order by average_shot_distance
select team, goals_per_shot, goals_per_shot_on_target, average_shot_distance from overall_wc_stats order by average_shot_distance desc;

#Write an SQL query to show team, errors, touches for which errors is 0 and touches is less than 1500
select team, errors, touches from overall_wc_stats where errors = 0 and touches < 1500;

#Write an SQL query to show team, fouls which has maximum number of fouls
select team, fouls from overall_wc_stats where fouls = (select max(fouls) from overall_wc_stats);

#Write an SQL query to show team, offisdes which has offsides less than 10 or greater than 20
select team, offsides from overall_wc_stats where offsides < 10 or offsides > 20;

#Write an SQL query to show team, aerials_won, aerials_lost, aerials_won_pct in descending order by aerials_won_pct
select team, aerials_won, aerials_lost, aerials_won_pct from overall_wc_stats order by aerials_won_pct;


#Write an SQL query to show number of teams each group has!
select `group` , count(team) from group_stage_team_stats group by `group`;

#Write a SQL query to show team names group 6 has
select team, `group` from group_stage_team_stats where `group` =6; 

#Write an SQL query to show Australia belongs to which group
select team, `group` from group_stage_team_stats where team='Australia';

#Write an SQL query to show group, average wins by each group
select `group`, avg(wins) from group_stage_team_stats group by `group`;

#Write an SQL query to show group, maximum expected_goal_scored by each group in ascending order by expected_goal_scored
select `group`, max(expected_goal_scored) from group_stage_team_stats group by `group` order by expected_goal_scored;

#Write an SQL query to show group, minimum exp_goal_conceded by each group in descending order by exp_goal_conceded
select `group`, min(exp_goal_conceded) from group_stage_team_stats group by `group` order by exp_goal_conceded desc;

#Write an SQL query to show group, average exp_goal_difference_per_90 for each group in ascending order by exp_goal_difference_per_90
select `group`, avg(exp_goal_difference_per_90) from group_stage_team_stats group by `group` order by exp_goal_difference_per_90;

#Write an SQL query to show which team has equal number of goals_scored and goals_against
select team,  goals_scored, goals_against from group_stage_team_stats where goals_scored = goals_against; 


#Write an SQL query to show which team has maximum players_used
select team, players_used from overall_wc_stats where players_used = (select max(players_used) from overall_wc_stats);

#Write an SQL query to show team, players_used, avg_age, games, minutes where minutes lessthan 500 and greater than 200
select team, players_used, avg_age, games, minutes from overall_wc_stats where minutes < 500 and minutes >200; 

#Write an SQL query to show all data of group_stats in ascending order BY points
select * from group_stage_team_stats order by points;

#Write an SQL query to show ALL UNIQUE team in ascending order by team
select distinct(team) from overall_wc_stats order by team;

#Write an SQL query to show average avg_age of each group and arrange it in descending order by avg_age.
select gs.`group`, avg(td.avg_age) as avg_gp_age from overall_wc_stats td inner join 
group_stage_team_stats gs on td.team = gs.team group by gs.`group` order by avg_gp_age desc;

#Write an SQL query to show sum of fouls for each group and arrange it in ascending order by fouls.
select gs.`group`, sum(td.fouls) as sum_fouls from overall_wc_stats td inner join group_stage_team_stats gs on td.team = gs.team group by gs.`group` order by sum_fouls;

select * from overall_wc_stats;
select * from group_stage_team_stats;

#Write an SQL query to show total number of games for each group and arrange it in descending order by games. 
select gs.`group`, sum(td.games) total_games from overall_wc_stats td inner join group_stage_team_stats gs
on td.team = gs.team group by gs.`group` order by total_games desc;

#Write an SQL query to show total number of players_used for each group and arrange it in ascending order by players_used. 
select gs.`group`, sum(td.players_used) Total_players from overall_wc_stats td inner join group_stage_team_stats gs
on td.team = gs.team group by gs.`group` order by Total_players;

#Write an SQL query to show total number of offsides for each group and arrange it in ascending order by offsides.
select gs.`group`, sum(td.offsides) Sum_offsides from overall_wc_stats td inner join group_stage_team_stats gs
on td.team=gs.team group by gs.`group` order by Sum_offsides;

#Write an SQL query to show average passes_pct for each group and arrange it in descending order by passes_pct.
select gs.`group`, avg(td.passes_pct) avg_pct from overall_wc_stats td inner join group_stage_team_stats gs
on td.team = gs.team group by gs.`group` order by avg_pct desc;

#Write an SQL query to show average goals_per90 for each group and arrange it in ascending order by goals_per90.
select gs.`group`, avg(td.goals_per90) avg_goal from overall_wc_stats td inner join group_stage_team_stats gs 
on td.team = gs.team group by gs.`group` order by avg_goal;















