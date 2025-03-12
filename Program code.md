# Program code
1. [Tournament selection](#tournament-selection)
2. [Proportional selection](#proportional-selection)
3. [Stochastic universal sampling selection](#stochastic-universal-sampling-selection)
4. [Rank selection](#rank-selection)
5. [Elite selection](#elite-selection)

- Tournament selection
    - Population create
        
        ```python
        import random
        from ch3.selection_tournament import selection_tournament
        from ch3.individual import Individual
        
        # 초기 설정
        POPULATION_SIZE = 5
        
        # 유전 알고리즘 흐름
        random.seed(18)
        
        # 첫 번째 개체군 생성
        population = Individual.create_random_population(POPULATION_SIZE)
        
        # 선택
        selected = selection_tournament(population, group_size=3)
        
        # 결과 출력
        print(f"Population: {population}")
        print(f"Selected: {selected}")
        ```
        
        - ch3
            - individual
                
                ```python
                import random
                
                class Individual:
                    def __init__(self, name: str, fitness: int) -> None:
                        self.name = name
                        self.fitness = fitness
                
                    def __repr__(self):
                        return f"{self.name}: {self.fitness}"
                
                    @classmethod
                    def create_random(cls, name: str) -> 'Individual':
                        # 예시로 임의의 fitness 값을 설정 (1~10)
                        fitness = random.randint(1, 10)
                        return cls(name, fitness)
                
                    @classmethod
                    def create_random_population(cls, size: int) -> list['Individual']:
                        # 개체군을 생성할 이름들 (A, B, C, D, E)
                        # names = ['A', 'B', 'C', 'D', 'E']         # 얘 때문에 기존 코드로 실행시 개체군이 5개 밖에 나오지 않는 문제 발생
                        names = [chr(65 + i) for i in range(size)]  # 얘로 바꾸니 해결 됨 65는 'A'의 ASCII 코드
                        return [cls.create_random(name) for name in names[:size]]
                ```
                
            - selection_tournament
                
                ```python
                import random
                
                 def selection_tournament(population, group_size):
                    selected = []
                    for _ in range(len(population)):
                        candidates = [random.choice(population) for _ in range(group_size)]
                        selected.append(max(candidates, key = lambda ind: ind.fitness))
                    return selected
                ```
                
        - individual + selection tournament + create
            
            ```python
            import random
            
            class Individual:
                def __init__(self, name: str, fitness: int) -> None:
                    self.name = name
                    self.fitness = fitness
            
                def __repr__(self):
                    return f"{self.name}: {self.fitness}"
            
                @classmethod
                def create_random(cls, name: str) -> 'Individual':
                    # 예시로 임의의 fitness 값을 설정 (1~10)
                    fitness = random.randint(1, 10)
                    return cls(name, fitness)
            
                @classmethod
                def create_random_population(cls, size: int) -> list['Individual']:
                    # 개체군을 생성할 이름들 (A, B, C, D, E)
                    names = ['A', 'B', 'C', 'D', 'E']
                    return [cls.create_random(name) for name in names[:size]]
                
            def selection_tournament(population, group_size):
                selected = []
                for _ in range(len(population)):
                    # tournament_size만큼 그룹을 랜덤으로 선택
                    candidates = [random.choice(population) for _ in range(group_size)]
                    # 그룹에서 fitness가 가장 큰 개체를 선택
                    selected.append(max(candidates, key = lambda ind: ind.fitness))
                return selected
            
            # 초기 설정
            POPULATION_SIZE = 5
            
            # 유전 알고리즘 흐름
            random.seed(4)
            
            # 첫 번째 개체군 생성
            population = Individual.create_random_population(POPULATION_SIZE)
            
            # 선택
            selected = selection_tournament(population, group_size=3)
            
            # 결과 출력
            print(f"Population: {population}")
            print(f"Selected: {selected}")
            ```
            
        - Result
            
            ![tournamentpopcreate](https://github.com/hwi-ya/Genetic-Algorithm/blob/783333cdf2c36891b28439ca021ad3f40b00ff5b/image.png)
            
    - Visualization
        
        ```python
        import random
        import pandas as pd
        import matplotlib.pyplot as plt
        from ch3.individual import Individual
        
        # 개체군 크기
        POPULATION_SIZE = 10
        # 서브그룹 크기?
        TOURNAMENT_SIZE = 3
        
        # 개체군 생성
        population = Individual.create_random_population(POPULATION_SIZE)
        
        # 토너먼트 후보 선택
        candidates = [random.choice(population) for _ in range(TOURNAMENT_SIZE)]
        
        # 후보 중 최고 개체 선택
        best = [max(candidates, key=lambda ind: ind.fitness)]
        
        # 개체 시각화 함수
        def plot_individuals(individual_set):
            df = pd.DataFrame({
                'name': [ind.name for ind in individual_set],
                'fitness': [ind.fitness for ind in individual_set]
            })
            df.plot.bar(x='name', y='fitness', rot=0)
            plt.show()
        
        # 개체군, 후보군, 최고 개체 시각화
        plot_individuals(population)
        plot_individuals(candidates)
        plot_individuals(best)
        ```
        
        - Result
            - Population
                
                ![image.png](image%201.png)
                
            - Candidates
                
                ![image.png](image%202.png)
                
            - Best
                
                ![image.png](image%203.png)
                
- Proportional selection
    - Population create
        
        ```python
        import random
        from ch3.selection_proportional import selection_proportional  # 비례 선택 함수 불러오기
        from ch3.individual import Individual  # Individual 클래스 불러오기
        
        POPULATION_SIZE = 9  # 개체군 크기 설정
        random.seed(4)  # 난수 시드 고정 (동일한 난수를 반복적으로 생성하기 위해)
        
        # 개체군 생성
        population = Individual.create_random_population(POPULATION_SIZE)  # 개체군을 랜덤하게 생성
        
        # 비례 선택(룰렛 휠 선택) 방식으로 개체 선택
        selected = selection_proportional(population)  # 선택된 개체는 룰렛 휠 선택 방식으로 뽑힘
        
        # 개체군과 선택된 개체 출력
        print(f"Population: {population}")  # 생성된 전체 개체군 출력
        print(f"Selected: {selected}")  # 선택된 개체들 출력
        ```
        
        - Result
            
            ![image.png](image%204.png)
            
    - Visualization
        - Bar graph ver.
            
            ```python
            import random
            import pandas as pd
            import matplotlib.pyplot as plt
            from ch3.individual import Individual  # 개체 클래스(유전자 알고리즘에서 개체를 나타냄) 불러오기
            
            # 난수 시드 설정 (항상 동일한 난수 발생) -> 같은 결과를 재현 가능하게 함
            random.seed(9)
            
            # 개체 수 설정
            POPULATION_SIZE = 5
            
            # 랜덤한 개체 생성 (유전자 알고리즘에서 초기 개체군 생성)
            unsorted_population = Individual.create_random_population(POPULATION_SIZE)
            
            # 개체를 fitness 값(적합도)에 따라 내림차순 정렬 (높을수록 좋은 개체)
            population = sorted(unsorted_population, key=lambda ind: ind.fitness, reverse=True)
            
            # 개체군 확인 코드 
            # for ind in population:
            #     print(ind.name, ind.fitness)
            
            # 전체 개체군의 fitness 합계 계산
            fitness_sum = sum([ind.fitness for ind in population])
            
            # 개체별 fitness 값을 저장할 딕셔너리 초기화
            fitness_map = {}
            
            # 각 개체의 fitness 값을 기반으로 선택 확률 계산
            for i in population:
                i_prob = round(100 * i.fitness / fitness_sum)  # 선택 확률을 백분율(%)로 변환
                i_label = f'{i.name} | fitness: {i.fitness}, prob: {i_prob}%'  # 개체 정보 문자열 생성
                fitness_map[i_label] = i.fitness  # 딕셔너리에 저장 (key: 개체 정보, value: fitness 값)
            
            # 데이터프레임 생성 (개체별 fitness 값을 저장)
            index = ['Sectors']
            df = pd.DataFrame(fitness_map, index=index)
            
            # 수평 막대 그래프 생성 (개체들의 fitness 비율을 시각화)
            df.plot.barh(stacked=True)
            
            # 룰렛 휠 선택 방식 시각화 (랜덤한 위치에 수직선 추가)
            for _ in range(POPULATION_SIZE):
                plt.axvline(x=random.random() * fitness_sum, linewidth=5, color='black')
            
            # x축 눈금 제거 (가독성 향상)
            plt.tick_params(axis='x', which='both', bottom=False, top=False, labelbottom=False)
            
            # 그래프 표시
            plt.show()
            ```
            
        - Pie graph ver.
            
            ```python
            import random
            import pandas as pd
            import matplotlib.pyplot as plt
            from ch3.individual import Individual  # 개체 클래스(유전자 알고리즘에서 개체를 나타냄) 불러오기
            
            # 난수 시드 설정 (항상 동일한 난수 발생) -> 같은 결과를 재현 가능하게 함
            random.seed(9)
            
            # 개체 수 설정
            POPULATION_SIZE = 5
            
            # 랜덤한 개체 생성 (유전자 알고리즘에서 초기 개체군 생성)
            unsorted_population = Individual.create_random_population(POPULATION_SIZE)
            
            # 개체를 fitness 값(적합도)에 따라 내림차순 정렬 (높을수록 좋은 개체)
            population = sorted(unsorted_population, key=lambda ind: ind.fitness, reverse=True)
            
            # 전체 개체군의 fitness 합계 계산
            fitness_sum = sum([ind.fitness for ind in population])
            
            # 개체별 fitness 값을 저장할 딕셔너리 초기화
            fitness_map = {}
            
            # 각 개체의 fitness 값을 기반으로 선택 확률 계산
            for i in population:
                i_prob = round(100 * i.fitness / fitness_sum)  # 선택 확률을 백분율(%)로 변환
                i_label = f'{i.name} | fitness: {i.fitness}, prob: {i_prob}%'  # 개체 정보 문자열 생성
                fitness_map[i_label] = i.fitness  # 딕셔너리에 저장 (key: 개체 정보, value: fitness 값)
                
            # 1. 각 개체의 선택 확률
            probabilities = [i.fitness / fitness_sum for i in population]
            
            # 2. 원그래프 시각화 (룰렛휠 방식)
            fig, ax = plt.subplots(figsize=(7, 7))
            
            # 원그래프에 각 개체의 영역을 표시
            ax.pie(probabilities, labels=[f'{i.name} | {i.fitness}' for i in population], autopct='%1.1f%%', startangle=90)
            
            # 그래프 스타일 설정
            ax.axis('equal')  # 원이 완전한 원 형태로 나오게 함
            plt.title("Roulette Wheel Selection Visualization")
            plt.show()
            ```
            
        - Result
            
            ![image.png](image%205.png)
            
    - ch3
        - individual
            
            ```python
            import random
            
            class Individual:
                def __init__(self, name: str, fitness: int) -> None:
                    self.name = name
                    self.fitness = fitness
            
                def __repr__(self):
                    return f"{self.name}: {self.fitness}"
            
                @classmethod
                def create_random(cls, name: str) -> 'Individual':
                    # 예시로 임의의 fitness 값을 설정 (1~10)
                    fitness = random.randint(1, 10)
                    return cls(name, fitness)
            
                @classmethod
                def create_random_population(cls, size: int) -> list['Individual']:
                    # 개체군을 생성할 이름들 (A, B, C, D, E)
                    # names = ['A', 'B', 'C', 'D', 'E']         # 얘 때문에 기존 코드로 실행시 개체군이 5개 밖에 나오지 않는 문제 발생
                    names = [chr(65 + i) for i in range(size)]  # 얘로 바꾸니 해결 됨 65는 'A'의 ASCII 코드
                    return [cls.create_random(name) for name in names[:size]]
            ```
            
        - selection_proportioanl
            
            ```python
            import random
            
            def selection_proportional(individuals):
                
                # 개체군을 fitness 값 기준으로 내림차순 정렬 (적합도가 높은 개체가 앞쪽)
                sorted_individuals = sorted(individuals, key=lambda ind: ind.fitness, reverse=True)
                
                # 전체 fitness 값의 합을 계산 (룰렛 휠의 전체 크기)
                fitness_sum = sum(ind.fitness for ind in individuals)
                
                # 선택된 개체를 저장할 리스트
                selected = []
            
                # 전체 개체 수만큼 반복하여 개체 선택
                for _ in range(len(sorted_individuals)):
                    # 0과 fitness_sum 사이의 무작위 값 생성 (룰렛 휠에서 화살표 역할)
                    shave = random.random() * fitness_sum
                    roulette_sum = 0  # 룰렛 휠의 현재 값 초기화
            
                    # 룰렛 휠을 돌려 선택 과정 수행
                    for ind in sorted_individuals:
                        roulette_sum += ind.fitness  # 현재 개체의 fitness 값을 누적
            
                        # 누적 fitness 값이 무작위로 선택된 값(shave)을 초과하면 해당 개체 선택
                        if roulette_sum > shave:
                            selected.append(ind)
                            break  # 한 개체를 선택했으므로 내부 루프 종료
            
                # 선택된 개체 리스트 반환
                return selected
            ```
            
- Stochastic universal sampling selection
    - Population create
        
        ```
        import random
        from ch3.selection_stochastic_universal_sampling import selection_stochastic_universal_sampling
        from ch3.individual import Individual
        
        POPULATION_SIZE = 5  # 개체군의 크기 설정
        random.seed(1)  # 난수 시드를 고정하여 동일한 난수 생성
        
        # 개체군 생성
        population = Individual.create_random_population(POPULATION_SIZE)
        
        # Stochastic Universal Sampling (SUS) 방식으로 개체 선택
        selected = selection_stochastic_universal_sampling(population)
        
        # 개체군과 선택된 개체 출력
        print(f"Population: {population}")  # 생성된 개체군 출력
        print(f"Selected: {selected}")  # 선택된 개체들 출력
        
        ```
        
    - Visualization
        - Bar gragh ver.
            
            ```python
            import random
            import pandas as pd
            import matplotlib.pyplot as plt
            from ch3.individual import Individual
            
            POPULATION_SIZE = 5
            random.seed(9)
            
            # 랜덤한 개체 생성
            unsorted_population = Individual.create_random_population(POPULATION_SIZE)
            
            # 개체를 fitness 값에 따라 내림차순으로 정렬
            population = sorted(unsorted_population, key=lambda ind: ind.fitness, reverse=True)
            
            # 전체 개체군의 fitness 합계 계산
            fitness_sum = sum([ind.fitness for ind in population])
            
            # 개체별 fitness 값을 저장할 딕셔너리 초기화
            fitness_map = {}
            for i in population:
                i_prob = round(100 * i.fitness / fitness_sum)  # 선택 확률을 백분율로 변환
                i_label = f'{i.name} | fitness: {i.fitness}, prob: {i_prob}%'  # 개체 정보 문자열 생성
                fitness_map[i_label] = i.fitness  # 딕셔너리에 저장 (key: 개체 정보, value: fitness 값)
            
            # 막대그래프
            # DataFrame을 사용하여 막대그래프를 그리기 위한 데이터 준비
            index = ['Sectors']
            df = pd.DataFrame(fitness_map, index=index)
            
            df.plot.barh(stacked=True)
            
            # 확률적 보편 샘플링을 위한 거리 계산
            distance = fitness_sum / POPULATION_SIZE
            shift = random.random() * distance  # 이동 거리 설정
            
            # 룰렛 휠을 나타내는 세로선 추가
            for i in range(POPULATION_SIZE):
                plt.axvline(x=shift + distance * i, linewidth=5, color='black')
            
            # x축 레이블 숨기기
            plt.tick_params(axis='x', which='both', bottom=False, top=False, labelbottom=False)
            
            # 그래프 출력
            plt.show()
            ```
            
        - Pie gragh ver.
            
            ```python
            import random
            import pandas as pd
            import matplotlib.pyplot as plt
            from ch3.individual import Individual
            
            POPULATION_SIZE = 5
            random.seed(9)
            
            # 랜덤한 개체 생성
            unsorted_population = Individual.create_random_population(POPULATION_SIZE)
            
            # 개체를 fitness 값에 따라 내림차순으로 정렬
            population = sorted(unsorted_population, key=lambda ind: ind.fitness, reverse=True)
            
            # 전체 개체군의 fitness 합계 계산
            fitness_sum = sum([ind.fitness for ind in population])
            
            # 개체별 fitness 값을 저장할 딕셔너리 초기화
            fitness_map = {}
            for i in population:
                i_prob = round(100 * i.fitness / fitness_sum)  # 선택 확률을 백분율로 변환
                i_label = f'{i.name} | fitness: {i.fitness}, prob: {i_prob}%'  # 개체 정보 문자열 생성
                fitness_map[i_label] = i.fitness  # 딕셔너리에 저장 (key: 개체 정보, value: fitness 값)
            
            # 원그래프
            labels = list(fitness_map.keys())
            sizes = list(fitness_map.values())
            
            # 원그래프
            plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
            plt.title("Fitness Distribution in Population")
            plt.show()
            ```
            
    - ch3
        - individual
            
            ```python
            import random
            
            class Individual:
                def __init__(self, name: str, fitness: int) -> None:
                    self.name = name
                    self.fitness = fitness
            
                def __repr__(self):
                    return f"{self.name}: {self.fitness}"
            
                @classmethod
                def create_random(cls, name: str) -> 'Individual':
                    # 예시로 임의의 fitness 값을 설정 (1~10)
                    fitness = random.randint(1, 10)
                    return cls(name, fitness)
            
                @classmethod
                def create_random_population(cls, size: int) -> list['Individual']:
                    # 개체군을 생성할 이름들 (A, B, C, D, E)
                    # names = ['A', 'B', 'C', 'D', 'E']         # 얘 때문에 기존 코드로 실행시 개체군이 5개 밖에 나오지 않는 문제 발생
                    names = [chr(65 + i) for i in range(size)]  # 얘로 바꾸니 해결 됨 65는 'A'의 ASCII 코드
                    return [cls.create_random(name) for name in names[:size]]
            ```
            
        - selection_stochastic_universal_sampling
            
            ```python
            import random
            
            def selection_stochastic_universal_sampling(individuals):
                # 개체들을 fitness 값에 따라 내림차순 정렬
                sorted_individuals = sorted(individuals, key=lambda ind: ind.fitness, reverse=True)
            
                # 전체 fitness 값의 합 계산
                fitness_sum = sum([ind.fitness for ind in individuals])
            
                # 거리 계산 (전체 fitness 값 합을 개체 수로 나누기)
                distance = fitness_sum / len(individuals)
            
                # 이동 거리 계산 (랜덤으로 설정)
                shift = random.uniform(0, distance)
            
                # 선택의 경계값들 계산 (각각의 경계에 해당하는 확률값을 계산)
                borders = [shift + i * distance for i in range(len(individuals))]
            
                selected = []
            
                # 경계값을 기준으로 개체를 선택
                for border in borders:
                    i = 0
                    roulette_sum = sorted_individuals[i].fitness
            
                    # 해당 경계값을 넘는 개체를 선택
                    while roulette_sum < border:
                        i += 1
                        roulette_sum += sorted_individuals[i].fitness
                    
                    # 선택된 개체를 추가
                    selected.append(sorted_individuals[i])
            
                return selected
            
            ```
            
    - Result
        
        ![image.png](image%206.png)
        
- Rank selection
    - Visualization
        
        ```python
        import random
        import pandas as pd
        import matplotlib.pyplot as plt
        from ch3.individual import Individual  # 개체 클래스 불러오기
        
        # 개체군의 크기 설정
        POPULATION_SIZE = 5
        random.seed(2)
        
        # 랜덤한 개체 생성
        unsorted_population = Individual.create_random_population(POPULATION_SIZE)
        population = sorted(unsorted_population, key=lambda ind: ind.fitness, reverse=True)
        
        # 전체 개체군의 fitness 합계 계산
        fitness_sum = sum([ind.fitness for ind in population])
        
        # 개체별 fitness 값을 저장할 딕셔너리 초기화
        fitness_map = {}
        
        # 각 개체의 fitness 값에 따라 선택 확률 계산
        for i in population:
            i_prob = round(100 * i.fitness / fitness_sum)  # 선택 확률을 백분율(%)로 변환
            i_label = f'{i.name} | fitness: {i.fitness}, prob: {i_prob}%'  # 개체 정보 문자열 생성
            fitness_map[i_label] = i.fitness  # 딕셔너리에 저장 (key: 개체 정보, value: fitness 값)
        
        # 데이터프레임 생성 (개체별 fitness 값을 저장)
        proportional_df = pd.DataFrame(fitness_map, index=['Sectors'])
        
        # 수평 막대 그래프 생성 (개체들의 fitness 비율을 시각화)
        proportional_df.plot.barh(stacked=True)
        plt.tick_params(axis='x', which='both', bottom=False, top=False, labelbottom=False)
        plt.title('Fitness Proportional Sectors')
        plt.show()
        
        # Rank 선택을 위한 비례 확률 계산
        rank_step = 1 / POPULATION_SIZE
        rank_sum = sum([1 - rank_step * i for i in range(len(population))])
        
        # 각 개체의 rank에 따른 선택 확률 계산
        rank_map = {}
        
        for i in range(len(population)):
            i_rank = i + 1  # 개체의 rank (1부터 시작)
            i_rank_proportion = 1 - i * rank_step  # rank에 따른 확률 비율 계산
            i_prob = round(100 * i_rank_proportion / rank_sum)  # 확률을 백분율(%)로 변환
            i_label = f'{population[i].name} | rank: {i_rank}, prob: {i_prob}%'  # 개체 정보 문자열 생성
            rank_map[i_label] = i_rank_proportion  # 딕셔너리에 저장 (key: 개체 정보, value: rank에 따른 확률)
        
        # 데이터프레임 생성 (개체별 rank 확률 값을 저장)
        rank_df = pd.DataFrame(rank_map, index=['Sectors'])
        
        # 수평 막대 그래프 생성 (개체들의 rank 비율을 시각화)
        rank_df.plot.barh(stacked=True)
        plt.tick_params(axis='x', which='both', bottom=False, top=False, labelbottom=False)
        plt.title('Rank Proportional Sectors')
        plt.show()
        ```
        
        - Result
            - Fitness Proportional Sectors
                
                ![image.png](image%207.png)
                
            - Rank Proportional Sectors
                
                ![image.png](image%208.png)
                
    - Population create
        
        ```python
        import random
        from ch3.selection_rank import selection_rank
        from ch3.individual import Individual
        
        POPULATION_SIZE = 5  # 개체군 크기 설정
        random.seed(18)  # 난수 시드를 고정하여 동일한 난수 생성
        
        # 개체군 생성
        population = Individual.create_random_population(POPULATION_SIZE)
        
        # Rank Selection 방식으로 개체 선택
        selected = selection_rank(population)
        
        # 개체군과 선택된 개체 출력
        print(f'Population: {population}')  # 생성된 개체군 출력
        print(f'Selected: {selected}')  # 선택된 개체들 출력
        ```
        
        - 결과
            
            ![image.png](image%209.png)
            
    - ch3
        - individual
            
            ```python
            import random
            
            class Individual:
                def __init__(self, name: str, fitness: int) -> None:
                    self.name = name
                    self.fitness = fitness
            
                def __repr__(self):
                    return f"{self.name}: {self.fitness}"
            
                @classmethod
                def create_random(cls, name: str) -> 'Individual':
                    # 예시로 임의의 fitness 값을 설정 (1~10)
                    fitness = random.randint(1, 10)
                    return cls(name, fitness)
            
                @classmethod
                def create_random_population(cls, size: int) -> list['Individual']:
                    # 개체군을 생성할 이름들 (A, B, C, D, E)
                    # names = ['A', 'B', 'C', 'D', 'E']         # 얘 때문에 기존 코드로 실행시 개체군이 5개 밖에 나오지 않는 문제 발생
                    names = [chr(65 + i) for i in range(size)]  # 얘로 바꾸니 해결 됨 65는 'A'의 ASCII 코드
                    return [cls.create_random(name) for name in names[:size]]
            ```
            
        - selection_rank
            
            ```python
            import random
            
            def selection_rank(individuals):
                # 개체들을 fitness 값에 따라 내림차순 정렬
                sorted_individuals = sorted(individuals, key=lambda ind: ind.fitness, reverse=True)
            
                # 개체 수에 맞는 순위 간격 계산
                rank_distance = 1 / len(individuals)
                
                # 각 개체의 순위에 따른 선택 확률 계산
                ranks = [(1 - i * rank_distance) for i in range(len(individuals))]
            
                # 순위 확률의 총합 계산
                ranks_sum = sum(ranks)
                
                # 선택된 개체들을 저장할 리스트
                selected = []
                
                # 선택된 개체 수만큼 반복
                for _ in range(len(sorted_individuals)):
                    # 임의의 선택 지점 (룰렛 휠의 '샤브' 위치)
                    shave = random.random() * ranks_sum
                    
                    rank_sum = 0
                    
                    # 룰렛 휠을 돌리며 선택
                    for i in range(len(sorted_individuals)):
                        rank_sum += ranks[i]
                        if rank_sum > shave:
                            # 선택된 개체를 리스트에 추가
                            selected.append(sorted_individuals[i])
                            break
                            
                return selected
            ```
            
- Elite selection
    - Rank selection base
        - Population create
            
            ```python
            import random
            from ch3.selection_rank_with_elite import selection_rank_with_elite
            from ch3.individual import Individual
            
            POPULATION_SIZE = 5  # 개체군 크기 설정
            random.seed(3)  # 난수 시드 고정 (동일한 난수 생성)
            
            # 개체군 생성
            population = Individual.create_random_population(POPULATION_SIZE)
            
            # Rank selection with elite 방식으로 개체 선택 (elite_size=2로 상위 2개 개체는 무조건 선택)
            selected = selection_rank_with_elite(population, elite_size=2)
            
            # 생성된 개체군과 선택된 개체 출력
            print(f"Population: {population}")
            print(f"Selected: {selected}")
            
            ```
            
            - Result
                
                ![image.png](image%209.png)
                
        - ch3
            - individual
                
                ```python
                import random
                
                class Individual:
                    def __init__(self, name: str, fitness: int) -> None:
                        self.name = name
                        self.fitness = fitness
                
                    def __repr__(self):
                        return f"{self.name}: {self.fitness}"
                
                    @classmethod
                    def create_random(cls, name: str) -> 'Individual':
                        # 예시로 임의의 fitness 값을 설정 (1~10)
                        fitness = random.randint(1, 10)
                        return cls(name, fitness)
                
                    @classmethod
                    def create_random_population(cls, size: int) -> list['Individual']:
                        # 개체군을 생성할 이름들 (A, B, C, D, E)
                        # names = ['A', 'B', 'C', 'D', 'E']         # 얘 때문에 기존 코드로 실행시 개체군이 5개 밖에 나오지 않는 문제 발생
                        names = [chr(65 + i) for i in range(size)]  # 얘로 바꾸니 해결 됨 65는 'A'의 ASCII 코드
                        return [cls.create_random(name) for name in names[:size]]
                ```
                
            - selection_rank_with_elite
                
                ```python
                import random
                
                def selection_rank_with_elite(individuals, elite_size = 0):
                    # 1. 개체들을 fitness 값에 따라 내림차순으로 정렬
                    sorted_individuals = sorted(individuals, key = lambda ind: ind.fitness, reverse = True)
                    
                    # 2. rank 거리 계산 (전체 개체 수에 따라 거리 값 계산)
                    rank_distance = 1 / len(individuals)
                    
                    # 3. 각 개체의 rank 계산 (1 - rank_distance * i)
                    ranks = [(1 - i * rank_distance) for i in range(len(individuals))]
                    
                    # 4. 랭크 값의 합 계산
                    ranks_sum = sum(ranks)
                    
                    # 5. 엘리트 선택: 상위 elite_size 개체는 항상 선택
                    selected = sorted_individuals[0:elite_size]
                    
                    # 6. 나머지 개체들은 랭크 선택 방식으로 선택
                    for i in range(len(sorted_individuals) - elite_size):
                        # 랜덤 값 생성
                        shave = random.random() * ranks_sum
                        
                        # 선택할 개체를 결정하기 위한 누적 랭크 합
                        rank_sum = 0
                        
                        # 누적 랭크 합을 통해 해당 경계값을 넘는 개체 선택
                        for i in range(len(sorted_individuals)):
                            rank_sum += ranks[i]
                            if rank_sum > shave:
                                selected.append(sorted_individuals[i])  # 선택된 개체를 추가
                                break
                    
                    return selected
                
                ```
                
    - 원서에는 랭크 선택 기반의 엘리트 선택만 있는데 순수 엘리트 선택만 사용 할 수도 있고 다른 선택 기반으로도 가능
