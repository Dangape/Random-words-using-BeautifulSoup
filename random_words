import re
import urllib.request
from bs4 import*

url = "http://www.palabrasaleatorias.com/"

idioma_palavras = input('''
Escolha uma das opções de idioma abaixo:

1 - Português
2 - Inglês
3 - Italiano
4 - Francês
5 - Espanhol

Digite a opção escolhida:''')

if idioma_palavras == '1':
    idioma = 'palavras-aleatorias'
elif idioma_palavras == '2':
    idioma = 'random-words'
elif idioma_palavras == '3':
    idioma = 'parole-casuali'
elif idioma_palavras == '4':
    idioma = 'mots-aleatoires'
elif idioma_palavras == '5':
    idioma = 'index'

n_palavras = input("\nDigite quantas palavras você quer que sejam geradas:")
while int(n_palavras) > 10: #Coloquei essa restrição apenas pq o site não deixava gerar mais de 10 palavras
    print('No máximo 10 palavras podem ser geradas. Escolha um valor menor.')
    n_palavras = input("\nDigite quantas palavras você quer que sejam geradas:")

url = url + idioma + ".php?fs=" +  n_palavras

teste = urllib.request.urlopen(url).read()
data = teste.decode('utf-8') #Precisa de decodificação para que os acentos apareçam
soup = BeautifulSoup(data, "html.parser")

data1 = soup.find_all('div') #Encontra todas as tags <div> </div> e mostra em formato de lista
words = data1[1:] # pega somente os elemntos da lista que contém as palavras geradas

for i in range(0,int(n_palavras)):
    string = str(words[i]) #O contador vai passar por toda a lista e converter seus elementos em string
    m = re.search('<div style="font-size:3em; color:#6200C5;">', string)
    end = m.end()
    n = re.search('</div>', string)
    start = n.start()
    palavra = string[end:start]
    print(palavra)
