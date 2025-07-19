# Teste Prático em Golang

Este exercício consistiu em manipular um slice contendo números inteiros aleatórios no intervalo de 1 a 10, com os seguintes objetivos:

- Realizar a soma dos números no intervalo de **1 a 5**  
- Realizar a soma dos números no intervalo de **6 a 10**

Ao final, os dois resultados são exibidos no console.

---

## Descrição do Problema

Foi fornecido um slice contendo números inteiros organizados aleatoriamente. A tarefa era:

1. Separar os números em duas variáveis de acordo com o intervalo (1–5 e 6–10)  
2. Somar os valores de cada grupo separadamente  
3. Imprimir o resultado de ambas as somas

---

##  Criação das Variáveis

- numeros: slice com os valores fornecidos  
- ateCinco e cincoAteDez: slices auxiliares para armazenar os números de cada faixa  
- limite: variável com valor 5, usada como controle durante a soma  
- somaAteCinco e `somaCincoAteDez`: variáveis inteiras que armazenam os resultados das somas

---

## Lógica de Utilizada

Utilizei um laço **for** para percorrer todos os elementos do slice **numeros**.  
Durante cada iteração, uma estrutura condicional **if** foi utilizada para verificar a faixa do número atual:

- Se o número for **menor ou igual a 5**, ele é adicionado ao slice **ateCinco**  
- Se o número estiver **entre 6 e 10**, é adicionado ao slice **cincoAteDez**

---

## Somatória dos Valores

Para realizar a soma dos valores armazenados nos slices, implementei uma verificação com `if` para garantir que o índice não ultrapasse o tamanho do slice, evitando assim o erro:

> **`runtime error: index out of range`**

Esse tipo de erro ocorre quando tentamos acessar uma posição que não existe dentro do slice.

---

## Resultado Final

Por fim, os valores de cada grupo foram somados respeitando o limite definido (neste caso, até 5 elementos), e os resultados foram exibidos no console.

---

## Código-Fonte (Golang)

package main

import "fmt"

func main() {

	numeros := []int{2, 8, 3, 10, 5, 4, 7, 9, 1, 6} // lista de números de 1 a 10

	ateCinco := []int{} // variável de 1 até 5
	cincoAteDez := []int{} // variável de 6 até 10
	limite := 5 // variável para verificação
	somaAteCinco := 0
	somaCincoAteDez := 0
	

	for i := 0; i < len(numeros); i++ { // um loop onde passará por cada índice da lista
		if numeros[i] <= 5 { // números de 1 até 5
			ateCinco = append(ateCinco, numeros[i]) // adiciona os números encontrados lista e adiciona na variável ateCinco
		} else if numeros[i] >= 6 && numeros[i] <= 10 { // números de 6 até 10
			cincoAteDez = append(cincoAteDez, numeros[i]) // adiciona os números encontrados na lista e adiciona na variável cintoAteDez
		}
	}

	fmt.Println("Numeros ate 5:", ateCinco) // Números encontrados de 1 até 5
	fmt.Println("Numeros de 5 até 10:", cincoAteDez) // Números encontrados de 6 até 10

	if len(ateCinco) < limite { // analisa a lista para verificar se existe 5 elementos (1 até 5)
		limite = len(ateCinco) //verificação se a variável tem cinco elementos
	}

	if len(cincoAteDez) < limite {
		limite = len(cincoAteDez) // Mesma verificação que está acima
	}

	for i := 0; i < limite; i++ {
		somaAteCinco += ateCinco[i] // Somatória
	}

	for i := 0; i < limite; i++ {
		somaCincoAteDez += cincoAteDez[i] // Somatória
	}

	
	fmt.Println("Primeira Soma: ", somaAteCinco) // imprimir Valores
	fmt.Println("Segunda Soma: ", somaCincoAteDez) // imprimir Valores
}
