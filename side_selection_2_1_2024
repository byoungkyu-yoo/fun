import random
import streamlit as st

class Team:
    def __init__(self, name, port):
        self.name = name
        self.port = port

def has_played_before(team1_name, team2_name, previous_matches):
    return (team1_name, team2_name) in previous_matches or (team2_name, team1_name) in previous_matches

def main():
    # 팀 목록
    teams = [
        Team("DK", 3),
        Team("HLE", 1),
        Team("FLY", 1),
        Team("G2", 1),
        Team("T1", 3),
        Team("TES", 2)
    ]

    # 이전 매칭 정보
    previous_matches = [
        ("T1", "TES"),
        ("FLY", "DK"),
        ("G2", "HLE")
    ]

    # 버튼이 눌리면 코드를 실행
    if st.button('팀 추첨 실행'):
        random.shuffle(teams)
        positions = [None] * 6  # 포지션 1~6

        # 팀 배치
        st.write("팀 추첨 순서:")
        team1 = teams[0]
        positions[0] = team1
        st.write(f"1번째 뽑힌 팀: {team1.name} (포지션 1)")

        team2 = teams[1]
        if not has_played_before(team1.name, team2.name, previous_matches):
            positions[1] = team2
            st.write(f"2번째 뽑힌 팀: {team2.name} (포지션 2)")
        else:
            positions[2] = team2
            st.write(f"2번째 뽑힌 팀: {team2.name} (포지션 3)")

        team3 = teams[2]
        if positions[1] is None:
            positions[1] = team3
            st.write(f"3번째 뽑힌 팀: {team3.name} (포지션 2)")
        else:
            positions[2] = team3
            st.write(f"3번째 뽑힌 팀: {team3.name} (포지션 3)")

        team4 = teams[3]
        if not has_played_before(positions[2].name, team4.name, previous_matches) and not has_played_before(teams[4].name, teams[5].name, previous_matches):
            positions[3] = team4
            st.write(f"4번째 뽑힌 팀: {team4.name} (포지션 4)")
        else:
            positions[4] = team4
            st.write(f"4번째 뽑힌 팀: {team4.name} (포지션 5)")

        team5 = teams[4]
        if positions[3] is None:
            positions[3] = team5
            st.write(f"5번째 뽑힌 팀: {team5.name} (포지션 4)")
        else:
            positions[4] = team5
            st.write(f"5번째 뽑힌 팀: {team4.name} (포지션 5)")

        team6 = teams[5]
        positions[5] = team6
        st.write(f"6번째 뽑힌 팀: {team6.name} (포지션 6)")

        st.write("\n매칭 결과:")
        matches = [
            (positions[0], positions[1]),  
            (positions[2], positions[3]),  
            (positions[4], positions[5])   
        ]

        def side_selection(name):
            return f"진영선택권: {name}"
        for idx, (team_a, team_b) in enumerate(matches, start=1):
            if team_a.port < team_b.port:
                side_choice = side_selection(team_a.name)
            elif team_a.port > team_b.port:
                side_choice = side_selection(team_b.name)
            else:
                pick_order_a = teams.index(team_a)
                pick_order_b = teams.index(team_b)
                if pick_order_a < pick_order_b:
                    side_choice = side_selection(team_a.name)
                else:
                    side_choice = side_selection(team_b.name)
            st.write(f"{team_a.name} vs {team_b.name} -> {side_choice}")

if __name__ == '__main__':
    main()
