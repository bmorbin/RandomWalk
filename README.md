
![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` python
import numpy as np
import matplotlib.pyplot as plt

# Definindo a semente de pseudo-aleatorização
np.random.seed(314)

# Sequência de v.a's de Bernoulli transformadas em -1 e +1
seq1 = [i if i==1 else -1 for i in np.random.randint(2, size=900)]
seq2 = [i if i==1 else -1 for i in np.random.randint(2, size=900)]
seq3 = [i if i==1 else -1 for i in np.random.randint(2, size=900)]

# Inserindo S0 = 0 para cada uma das 3 sequências
seq1.insert(0,0)
seq2.insert(0,0)
seq3.insert(0,0)

# Soma acumulativa para gerar a sequência {Sn}
road1 = np.cumsum(seq1)
road2 = np.cumsum(seq2)
road3 = np.cumsum(seq3)

# Lista dos estados de tempo (de 0 a 900)
n_seq = list(range(901))

# Criação e exibição do gráfico
plt.style.use("ggplot")
fig,ax = plt.subplots()

ax.plot(n_seq,road1, c='#E66625', linestyle='--')
ax.plot(n_seq,road2, c='#15E65B', linestyle=':')
ax.plot(n_seq,road3, c='#0D0EE6', linestyle="-")
ax.axhline(y=0, color='white')
plt.xlim([0,900])
lim_y = max(-min(min(road1),min(road2),min(road3)),max(max(road1),max(road2),max(road3)))+10
plt.ylim([-lim_y,+lim_y])

ax.set_xlabel('n')
ax.set_ylabel('Sn')
ax.set_title("Random Walk Simulation - 3 Roads")

plt.show()
```

