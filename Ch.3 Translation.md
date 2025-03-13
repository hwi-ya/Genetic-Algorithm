# Translation
 - [README](https://github.com/hwi-ya/Genetic-Algorithm/blob/main/README.md)
## INDEX
<details>
  <summary>INDEX</summary>
 
   [p.1 (selection)](#p1-selection) <br>
   [p.2 (selection)](#p2-selection) <br>
   [p.3 (selection methods)](#p3-selection-methods) <br>
   [p.4 (Tournament selection)](#p4-tournament-selection) <br>
   Page.5 <br>
   [p.6 (Tournament selection)](#p6-tournament-selection) <br>
   [p.7 (Proportional selection)](#p7-proportional-selection) <br>
   Page.8 <br>
   [p.9 (Stochastic universal sampling selection)](#p9-Stochastic-universal-sampling-selection) <br>
   [p.10 (Stochastic universal sampling selection)](#p10-Stochastic-universal-sampling-selection) <br>
   [p.11 (Rank selection)](#p11-Rank-selection) <br>
   [p.12 (Rank selection)](#p12-Rank-selection) <br>
   Page.13 <br>
   [p.14 (Elite selection)](#p14-Elite-selection) <br>
   [Original Book p.111 (Elite selection)](#Original-Book-p111-Elite-selection) <br>
   [Original Book p.112 (Conclusion)](#Original-Book-p112-Conclusion) <br>
   [Original Book p.113 (Points to remember)](#Original-Book-p113-Points-to-remember) <br>
 
</details>
<br>

- ## p.1 (selection)
    - Selection is the choice of those individuals that will participate in creating offspring for the next population, that is, for the next generation.
        
        ---
        
        Selection is the choice of those individuals <br>
        selection은 개체들의 선택이다<br>
        
        that will participate in creating offspring <br>
        다음 인구를 위해 자식을 만드는데 참여할 <br>
        
        that is, for the next generation <br>
        즉, 다음 세대를 위한 과정이다 <br>
        
        ---
        
        selection은 다음 세대를 위해 자식을 만드는데 참여할 개체들을 선택하는 것 이다. 즉, 다음 세대를 위한 과정이다 <br>
        
        ---
        
        offspring - 자식
      
        <br>
              
    - Such a choice is made by the principle of natural selection, according to which the most adapted individuals have the highest chances of participating in the creation of new individuals.
        
        ---
        
        Such a choice is made by the principle of natural selection, <br>
        이러한 선택은 다음과 같은 자연 선택 원칙에 의해 만들어졌다 <br>
        
        according to which the most adapted individuals <br>
        그에 따르면 가장 적응된 개체들이 <br>
        
        have the highest chances <br>
        가장 높은 기회?가능성? 확률? 을 갖는다 <br>
        
        of participating <br>
        참여할 <br>
        
        in the creation of new individuals. <br>
        새로운 개체를 만드는 것에 <br>
        
        ---
        
        이러한 선택은 자연 선택 원칙에 의해 이루어지며 가장 적응된 개체들이 새로운 개체를 만드는 것에 참여할 가장 높은 기회를 갖는다
        
        ---
        
        적응된 개체가 어색하니 적응력이 높은 정도로 의역하기
      
        <br>
        
    - As a result, an intermediate population (or parent pool) appears. An intermediate population is a set of individuals that have acquired the right to breed
        
        ---
        
        As a result, <br>
        그 결과<br>
        
        an intermediate population (or parent pool) appears <br>
        중간 집단(혹은 부모 풀(웅덩이))이 발생한다 <br>
        
        An intermediate population is a set <br>
        이 중간집단은 집합이다 <br>
        
        of individuals that have acquired the right to breed <br>
        번식할?사육할 권한을 획득한 개인의 <br>
        
        ---
        
        그 결과, 중간집단(혹은 부모 풀)이 발생한다. 이 중간집단은 번식할 권한을 획득한 개체들의 집합이다 <br>
        
        <br>
        
    - Adapted individuals can be recorded there several times. The abandoned individuals will most likely not get there at all.
        
        ---
        
        Adapted individuals can be recorded there several times. <br>
        적응력이 높은 개체는 여러번 기록될 수 있다. <br>
        
        The abandoned individuals will most likely not get there at all. <br>
        버려진 개체들은 그곳에 아예 포함되지 못 할 수도 있다 <br>
        
        ---
        
        적응력이 높은 개체들은 여러번 기록될 수 있고 버려진 개체들은 그곳에 아예 포함되지 못 할 수도 있다.
        
        ---
        
        포함되지 못 할 수도 있다보다 포함되지 않을 수 있다 로 의역
        
        <br>
  
        [Main](#index)
      
- ## p.2 (selection)
    - NOTE: It is important to understand that the same individual can be selected several times by the selection method, which means it can repeatedly participate in the process of creating new individuals.
        
        ---
        
        NOTE: It is important to understand <br>
        참고 : 이해하는 것이 중요하다 <br>
        
         that the same individual can be selected several times by the selection method, <br>
        같은 객체가 여러번 선택될 수 있다 선택방법에 의해 <br>
        
        which means it can repeatedly participate in the process of creating new individuals. <br>
        즉, 반복적으로 참여할 수 있다 새로운 개체를 만드는 과정에 <br>
        
        ---
        
        참고 : 같은 객체가 선택 방법에 의해 여러번 선택될 수 있다는 것을 이해하는 것이 중요하다. <br>        
        즉, 새로운 개체를 만드는 과정에 반복적으로 참여할 수 있다. 

        <br>

        [Main](#index)
      
- ## p.3 (selection methods)
    - selection methods <br>
      선택 방법 <br>
      
        Tournament selection <br>
        토너먼트 선택 <br>
        
        Proportional selection <br>
        비례 선택 <br>
        
        Stochastic universal sampling selection <br>
        확률적 보편 샘플링 선택 <br>
        
        Rank selection <br>
        순위 선택 <br>
        
        Elite selection <br>
        엘리트 선택 <br>
    
        <br>

        [Main](#index)
      
- ## p.4 (Tournament selection)
    - Tournament selection is one of the simplest selection methods, and we will start with it.
        
        ---
        
        Tournament selection is one of the simplest selection methods, <br>
        토너먼트 선택은 가장 간단한 선택 방법중 하나이며, <br>
        
        and we will start with it. <br>
        우리는 이것부터 시작할 것 이다. <br>
        
        ---
        
        토너먼트 선택은 가장 간단한 선택 방법중 하나이며, 우리는 이것부터 시작할 것이다.

      <br>
        
    - In tournament selection, a subgroup is selected in a population, and then the best individual in this subgroup is selected
        
        ---
        
        In tournament selection, a subgroup is selected in a population, <br>
        토너먼트 선택에서는 집단에서 서브그룹이 선택되고, <br>
        
        and then the best individual in this subgroup is selected <br>
        그후 우수한 개체가 서브그룹에서 선택된다 <br>
        
        ---
        
        토너먼트 선택에서는 집단에서 서브그룹이 선택되고, 그 후 우수한 개체가 서브그룹에서 선택된다.

      <br>
        
    - Typically, the size of a subgroup is 2 or 3 individuals
        
        ---
        
        일반적으로 서브그룹의 크기는 2개체 혹은 3개체 이다

        <br>
        
    - NOTE: It is worth mentioning that if the group size is two, then the worst individual will never be selected; if the group size is three, then the two worst individuals will never be selected, and so on
        
        ---
        
        NOTE: It is worth mentioning <br>
        참고 : 이것은 언급할 가치가 있다 <br>
        
        that if the group size is two, then the worst individual will never be selected; <br>
        만약 그룹 크기가 2라면 최악의 개체는 절대 선택되지 않는다 <br>
        
        if the group size is three, then the two worst individuals will never be selected, and so on <br>
        만약 그룹 크기가 3이라면 최악의 두 개체는 선택되지 않는다 등 <br>
        
        ---
        
        참고 : 이것은 언급할 가치가 있다 만약 그룹 크기가 2라면 최악의 개체는 절대 선택 되지 않으며  만약 그룹 크기가 3이라면 최악의 두 개체는 선택되지 않는다
        
        ---
        
        참고 : 이것은 언급할 가치가 있다 만약 그룹 크기가 2라면 최악의 개체는 절대 선택 되지 않으며  만약 그룹 크기가 3이라면 최악의 두 개체는 선택되지 않는다 이와 같은 방식으로 그룹 크기가 커질수록 선택되지 않는 개체의 수가 늘어난다. 정도로 번역하면 된다.

      <br>

      [Main](#index)
      
- ## p.5
    - [Main](#index)
      
- ## p.6 (Tournament selection)
    - As expected, two worst individuals, A and C were not selected.
        
        ---
        
        예상대로 최악의 두 개체인 A와 C는 선택되지 않았다.

      <br>
        
    - But we have one more interesting result – the individual D, which has the second fitness score, was also not selected.
        
        ---
        
        But we have one more interesting result <br>
        그러나 우리는 한가지 더 흥미로운 결과를 얻었다. <br>
        
        the individual D, which has the second fitness score, was also not selected <br>
        두번째 적합도 점수를 갖는 D개체 또한 선택되지 않았다 <br>
        
        ---
        
        그러나 우리는 한가지 더 흥미로운 결과를 얻었는데 두 번째 적합도 점수를 가진 D개체 또한 선택되지 않았다
        
        ---
        
        두 번째로 높은 적합도 점수를 가진 D개체 또한 선택되지 않았다 로 의역해도 될듯

      <br>
        
    - You always have to keep in mind that the tournament selection is a random process, and there is no 100% guarantee that the best individual will be selected
        
        ---
        
        You always have to keep in mind <br>
        명심해라 <br>
        
        that the tournament selection is a random process, <br>
        토너먼트 선택은 무작위 과정이기에, <br>
        
        and there is no 100% guarantee that the best individual will be selected <br>
        100% 보장할 수 없다 최고의 개체가 선택 될 것 이라고 <br>
        
        ---
        
        명심해야 할 점은 토너먼트 선택이 무작위 과정이기에, 최고의 개체가 선택 될 것이라고 100% 보장할 수 없다는 것이다
        
        or
        
        명심해라 토너먼트 선택은 무작위 과정이기에, 최고의 개체가 선택 될 것이라고 100% 보장할 수 없다.

      <br>

      [Main](#index)
      
- ## p.7 (Proportional selection)
    - This method can be illustrated with a roulette wheel.
        
        ---
        
        이 방법은 룰렛 휠로 설명할 수 있다
        
        <br>
        
    - Each individual is assigned a sector of the roulette wheel, the value of which is set proportional to the value of the fitness function of a given individual; therefore, the greater the value of the fitness function, the larger the sector on the roulette wheel.
        
        ---
        
        Each individual is assigned a sector of the roulette wheel, <br>
        각 개체는 배정 받는다 룰렛 휠의 섹터를 <br>
        
        the value of which is set proportional to the value of the fitness function of a given individual <br>
        그 값은 설정된다 주어진 개체의 적합도 함수 값에 비례하게 <br>
        
        therefore, the greater the value of the fitness function, the larger the sector on the roulette wheel. <br>
        그러므로, 적합도 함수의 값이 더 클수록, 룰렛 휠에서의 섹터도 더 커진다 <br>
        
        ---
        
        각 개체는 룰렛 휠의 섹터를 배정받으며, 그 값은 주어진 개체의 적합도 함수 값에 비례하게 설정된다. 그러므로, 적합도 함수의 값이 더 클수록, 룰렛 휠에서의 섹터도 더 커진다
        
        ---
        
        어쩄든 the value의 값이 룰렛 휠의 섹터니 섹터의 크기로 봐도 될듯

      <br>
        
    - From this, it follows that the larger the sector on the roulette wheel, the higher the chance that this particular individual will be chosen
        
        ---
        
        이로부터, 결론를 얻을 수 있다 룰렛휠의 섹터가 더 클수록, 확률이 높아진다 특정 개체가 선택될
        
        ---
        
        이로부터, 룰렛휠의 섹터가 더 클수록, 특정 개체가 선택될 확률이 더 높아진다는 결론을 얻을 수 있다.

      <br>

      [Main](#index)
      
- ## p.8 (p.7 내용 중복)
     - [Main](#index)
  
- ## p.9 (Stochastic universal sampling selection)
    - Stochastic universal sampling selection method is an alternative method of proportional selection.
        
        ---
        
        확률적 보편 샘플링 선택은 비례 선택의 대안방법이다.
        
        <br>
        
    - In this method, the entire roulette wheel is divided into N cutoffs with equal spacing
        
        ---
        
        이 방법은 전체 룰렛휠을 동일한 간격으로 N개의 cutoffs로 나뉜다

        <br>
        
    - This method smooths out the elements of randomness which
    proportional selection has, and ensures that the individuals are selected according to the following principle – many good individuals, some average individuals, and a few bad individuals.
        
        ---
        
        This method smooths out the elements of randomness which proportional selection has, <br>
        이 방법은 불규칙성을 없앤다 무작위성의 요소를 비례선택이 가지고 있는, <br>
        
        and ensures that the individuals are selected according to the following principle <br>
        그리고 보장한다  개체들이 선택되도록 다음 원칙에 따라 <br>
        
        many good individuals, some average individuals, and a few bad individuals. <br>
        많은 좋은 개체, 몇몇 평균 개체, 그리고 조금 나쁜 개체들 <br>
        
        ---
        
        이 방법은 비례선택이 가진 무작위성의 요소를 없앤다, 그리고 개체들이 다음 원칙에 따라 선택되도록 보장한다 - 많은 좋은 개체, 몇몇 평균 개체, 그리고 몇몇 나쁜 개체들이
        
        <br>

        [Main](#index)
      
- ## p.10 (Stochastic universal sampling selection)
    - As with the proportional selection method, the stochastic universal sampling selection has the possibility to select the worst individual, and also has the possibility to not select the best individual.
        
        ---
        
        As with the proportional selection method, <br>
        비례 선택 방법과 마찬가지로, <br>
        
        the stochastic universal sampling selection has the possibility to select the worst individual <br>
        확률적 보편 샘플링 선택도 선택할 가능성이 있다 최악의 개체를, <br>
        
        and also has the possibility to not select the best individual. <br>
        그리고 또한 가능성이 있다 최고의 개체를 선택하지 않을 <br>
        
        ---
        
        비례 선택 방법과 마찬가지로, 확률적 보편 샘플링도 최악의 개체를 선택할 가능성이 있고 또한 최고의 개체를 선택하지 않을 가능성이 있다.

        <br>
        
    - Even if it seems contradictory, this approach shows very good results for a particular class of problems.
        
        ---
        
        모순적인 것 처럼 보이지만, 이 접근법은 특정한 종류의 문제에 대해서 매우 좋은 결과를 보여준다

      <br>

      [Main](#index)
      
- ## p.11 (Rank selection)
    - Rank selection has the same principle as proportional selection, but individuals of the population are ranked according to the values of their fitness function.
        
        ---
        
        Rank selection has the same principle as proportional selection, <br>
        순위 선택은 동일한 원칙을 가진다 비례 선택과, <br>
        
        but individuals of the population are ranked according to the values of their fitness function. <br>
        그러나 그 집단의 개체들은 순위가 매겨진다 그들의 적합도 함수의 값에 따라서 <br>
        
        ---
        
        순위 선택은 비례 선택과 동일한 원칙을 가진다, 그러나 그 집단의 개체들은 그들의 적합도 함수 값에 따라서 순위가 매겨진다

      <br>
        
    - This can be thought of as a sorted list of individuals, ordered from the fittest to the least fit, in which each individual is assigned a number that determines its place in the list, called rank
        
        ---
        
        This can be thought of as a sorted list of individuals, <br>
        이것은 생각 할 수 있다 개체의 목록이 정렬된 것 으로 <br>
        
        ordered from the fittest to the least fit <br>
        가장 적합한 것부터 적합하지 않은 것까지 정렬된 <br>
        
        in which each individual is assigned a number that determines its place in the list, called rank <br>
        그곳에서 각 개체는 배정된다 번호가 그것은 결정한다 목록에서의 위치를, 순위라 불리는 <br>
        
        ---
        
        이것은 개체의 목록이 정렬된 것으로 생각 할 수 있다, 가장 적합한 것부터 적합하지 않은 것까지 정렬된, 그안에서 각 개체는 목록에서의 위치를 결정하는 번호를 배정받으며, 이를 순위라고 한다

      <br>
        
    - Rank selection smoothens out the large difference between individuals with high fitness values and individuals with low fitness values.
        
        ---
        
        랭크 선택은 높은 적합도 값을 가진 개체와 낮은 적합도 값을 가진 개체의 큰 차이를 완화시킨다

      <br>

      [Main](#index)
      
- ## p.12 (Rank selection)
    - the best individual in rank selection has a lower chance of being selected than it has in the proportional selection, and on the contrary, the worst individual, which had no chance of being selected in proportional selection has some positive probability of being selected.
        
        ---
        
        the best individual in rank selection has a lower chance of being selected than it has in the proportional selection <br>
        최고의 개체는 랭크선택에서 선택될 확률이 낮다 비례선택에서 보다 <br>
        
        and on the contrary, the worst individual, which had no chance of being selected in proportional selection has some positive probability of being selected. <br>
        그와 달리, 최악의 개체는 선택될 수 없었지만 비례선택에서는 일부 긍정적인 확률을 가진다 선택될
        
        ---
        
        최고의 개체는 비례선택에서 보다 랭크선택에서 선택될 확률이 낮은 반면 최악의 개체는 비례선택에서는 선택될 수 없었지만 선택될 일부 긍정적인 확률을 가진다

      <br>
        
    - 대충 그래프
        
        <br>
        
        [Main](#index)
      
- ## p.13 (Rank selection(How rank selection is calculated?))
     - [Main](#index)
    
- ## p.14 (Elite selection)
    - As we have already seen, none of the selection methods that we have considered – tournament, proportional, stochastic universal sampling, and rank selection –guarantee the selection of the best individual.
        
        ---
        
        As we have already seen <br>
        우리가 이미 보았듯이 <br>
        
        none of the selection methods that we have considered – tournament, proportional, stochastic universal sampling and rank selection – <br>
        우리가 고려한 어떠한 선택 방법도 -대충 지금까지 한거-
        
        guarantee the selection of the best individual. <br>
        최고의 개체의 선택을 보장하지 못했다 <br>
        
        ---
        
        우리가 이미 보았듯이 우리가 고려한 어떠한 선택 방법도 최고의 개체의 선택을 보장하지 않는다

      <br>
        
    - The genes of the best individual can be very valuable for the next
    generations, so there is an approach that protects the best individuals.
        
        ---
        
        The genes of the best individual can be very valuable for the next generations, <br>
        최고의 개체의 유전자는 다음 세대에게 매우 가치가 클 수 있다
        
        so there is an approach that protects the best individuals. <br>
        그래서 접근방법이 있다 최고의 개체를 보호하는
        
        ---
        
        최고 개체의 유전자는 다음 세대에게 매우 가치가 클 수 있다 그래서 최고의 개체를 보호하는 접근 방법이 있다
        
        ---
        
        대충 그래서 → 따라서로 해도 될듯

      <br>
        
    - This method is called elite Elite selection can be based on another method, such as rank selection, but the main change in this method is the guaranteed inclusion of the best individuals in the selected population.
        
        ---
        
        This method is called elite. Elite selection can be based on another method, such as rank selection, <br>
        이 방법은 엘리트라고 불린다 엘리트 선택은 다른 방법을 기반으로 할 수 있다 예를 들어 랭크선택과 같은 <br>
        
        but the main change in this method is the guaranteed inclusion of the best individuals in the selected population. <br>
        그러나  이 방법의 주요 변화는 보장한다 최고의 개체가 포함된다는 점을 선택된 집단에서 <br>
        
        ---
        
        이 방법은 엘리트라고 불린다. 엘리트 선택은 랭크선택과 같은 다른 방법을 기반으로 할 수 있다. 그러나 이방법의 주요 변화는 선택된 집단에서 최고의 개체가 포함된다는 것을 보장한다

      <br>

      [Main](#index)
      
- ## Original Book p.111 (Elite selection)
    - NOTE: Elite selection is a handy method of selection in conditions where an individual's fitness may degenerate as a result of crossover or mutation. We need to protect the best individuals, and try to spread their genes among the population.
        
        ---
        
        NOTE: Elite selection is a handy method of selection in conditions <br>
        참고 : 엘리트 선택은 유용한 선택방법이다 특정 조건에서 <br>
        
        where an individual's fitness may degenerate as a result of crossover or mutation. <br>
        개인의 적합도가 퇴화할 수 있는 상황에서 교차나 돌연변이의 결과로 <br>
        
        We need to protect the best individuals, and try to spread their genes among the population. <br>
        우리는 최고의 개체를 보호해야한다 그리고 퍼뜨리려고 노력해야한다 그들의 유전자가 개체군에 퍼지도록 <br>
        
        ---
        
        참고 : 엘리트 선택은 특정 조건(교차나 돌연변이의 결과로 개인의 적합도가 퇴화할 수 있는 상황에서)에서 유용한 선택방법이다.  우리는 최고의 개체를 보호해야하며, 그들의 유전자가 개체군에 퍼지도록 노력해야한다.

      <br>

      [Main](#index)
      
- ## Original Book p.112 (Conclusion)
    - Selection is a very important part of the evolution process; every individual aims to generate an offspring. The selection process is random by nature. We have studied several selection methods, each of which has its pros and cons. You can use one of these methods or any modification
        
        ---
        
        Selection is a very important part of the evolution process; <br>
        선택은 매우 중요한 부분이다 진화 과정에서 <br>
        
        every individual aims to generate an offspring. <br>
        모든 개체는 목표로 한다 자손을 생성하는 것을 <br>
        
        The selection process is random by nature. <br>
        선택과정은 랜덤이다 본질적으로 <br>
        
        We have studied several selection methods, each of which has its pros and cons. <br>
        우리는 연구했다 여러가지 선택 방법을, 각각의 방법은 가진다 장점과 단점을 <br>
        
        You can use one of these methods or any modification <br>
        너는 사용 할 수 있다 이 방법들중 하나 혹은 어떤 수정이라도 <br>
        
        ---
        
        선택은 진화 과정에서 매우 중요한 부분이다. 모든 개체는 자손을 생성하는 것을 목표로 한다. 선택과정은 본질적으로 랜덤이다. 우리는 여러가지 선택방법을 연구 했으며, 각각의 방법은 장단점이 있다. 너는 이러한 방법들중 하나나 어떤 수정이라도 사용할 수 있다.

        <br>

        [Main](#index)
      
- ## Original Book p.113 (Points to remember)
    - Each selection method has the following principle -- adapted individuals have a higher possibility to be selected than the abandoned ones.
        
        ---
        
        Each selection method has the following principle -- <br>
        각각의 선택 방법은 가지고 있다 다음의 원칙을 <br>
        
        adapted individuals have a higher possibility to be selected than the abandoned ones. <br>
        적응한 개체들은 가지고 있다 높은 가능성을 선택될 버려진 것들 보다 <br>
        
        ---
        
        각각의 선택방법은 다음의 원칙을 가지고 있다 -- 적응한 개체들은 버려진 개체보다 선택될 가능성이 더 높다

        <br>
        
    - Even abandoned individuals can have something valuable in their genes, so we have to leave a positive probability for them to be selected.
        
        ---
        
        Even abandoned individuals can have something valuable in their genes, <br>
        심지어 버려진 개체들도 가질 수 있다 가치있는 무언가를 그들의 유전자에 <br>
        
        so we have to leave a positive probability for them to be selected. <br>
        그래서 우리는 남겨둬야 한다 긍정적인 확률을 그들이 선택될 수 있도록 <br>
        
        ---
        
        심지어 버려진 개체들도 그들의 유전자에 가치있는 무언가를 가질 수 있다 그래서 우리는 그들이 선택될 수 있도록 긍정적인 확률을 남겨둬야 한다.

      <br>

      [Main](#index)
      
