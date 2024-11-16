# Greenwin
import random

# 設定球隊名稱
team_names = ["主隊雷霆", "客隊黃蜂", "邁阿密熱火", "金州勇士", "布魯克林籃網"]
home_team = team_names[0]
away_team = team_names[1]

# 設定主客隊平均得失分
home_avg_pts = 122.2
home_avg_opp_pts = 112.5
away_avg_pts = 109
away_avg_opp_pts = 121.1

# 設定先發球員得分
home_starters = {"A": 31.3, "B": 10.5, "C":
11.5, "D": 4.5,"E": 16.7}
away_starters = {"F": 5, "G": 21.1, "H":
7.3,"I": 15.3,"J": 9.6}

# 計算主客隊預測得分
home_predicted_pts = round((home_avg_pts + away_avg_opp_pts) / 2 + sum(home_starters.values()) / 5 * 1.5)
away_predicted_pts = round((away_avg_pts + home_avg_opp_pts) / 2 + sum(away_starters.values()) / 5 * 1.5)

# 計算讓分數
spread = home_predicted_pts - away_predicted_pts

# 計算大小分數
total_pts = home_avg_pts + away_avg_pts
if home_avg_pts > away_avg_pts:
    home_expected_pts = total_pts / 2 + spread / 2
else:
    home_expected_pts = total_pts / 2 - spread / 2
away_expected_pts = total_pts - home_expected_pts

# 進行比賽模擬
home_score = random.randint(max(0, home_predicted_pts - 15), home_predicted_pts + 15)
away_score = random.randint(max(0, away_predicted_pts - 15), away_predicted_pts + 15)

# 計算比賽結果
if home_score > away_score:
    winner = home_team
    loser = away_team
else:
    winner = away_team
    loser = home_team

# 輸出結果
print(f"{home_team}得分：{home_score}")
print(f"{away_team}得分：{away_score}")
print(f"預測比分：{home_team} {home_predicted_pts} - {away_team} {away_predicted_pts}")
print(f"讓分：{home_team}讓{spread}分")
print(f"本場大小分：{total_pts}, {home_team} {round(home_expected_pts,1)}, {away_team} {round(away_expected_pts,1)}")
print(f"勝者：{winner}")