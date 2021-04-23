import random
import math
from datetime import datetime

def decimal_a_binario(decimal):
    if decimal <= 0:
        return int("0")
    binario = ""
    while decimal > 0:
        residuo = int(decimal % 2)
        decimal = int(decimal / 2)
        binario = str(residuo) + binario
    return int(binario)

def convertir_a_lista(numero):
    num = decimal_a_binario(numero)
    digit_num = str(num)
    digit_map = map(int,digit_num)
    digit_list = list(digit_map)
    while len(digit_list)<5:
        digit_list.insert(0,0)
    return digit_list

def valor_decimal(lst):
    valor = 0
    for i in range(len(lst)):
        if lst[i] !=0:
            valor = 2**(len(lst)-1-i) + valor
    return valor

def calcular_energia(x):
    return x**3 - 60*(x**2) + 900*x+100

def energia(x):
    return calcular_energia(valor_decimal(x))

def funcion_aceptacion(new_energy, current_energy, temperatura):
        if new_energy < current_energy:
            return True
        elif random.uniform(0.000001,1.0) < math.exp(-((new_energy - current_energy) / temperatura)):
            return True
        return False
    
def generarListaAleatoria():
    random.seed(None,2)
    aleatorio = random.randint(0,30)
    listas = [[0,0,0,0,0],
              [0,0,0,0,1],
              [0,0,0,1,0],
              [0,0,0,1,1],
              [0,0,1,0,0],
              [0,0,1,0,1],
              [0,0,1,1,0],
              [0,0,1,1,1],
              [0,1,0,0,0],
              [0,1,0,0,1],
              [0,1,0,1,0],
              [0,1,0,1,1],
              [0,1,1,0,0],
              [0,1,1,0,1],
              [0,1,1,1,0],
              [0,1,1,1,1],
              [1,0,0,0,1],
              [1,0,0,1,0],
              [1,0,0,1,1],
              [1,0,1,0,0],
              [1,0,1,0,1],
              [1,0,1,1,0],
              [1,0,1,1,1],
              [1,1,0,0,0],
              [1,1,0,0,1],
              [1,1,0,1,0],
              [1,1,0,1,1],
              [1,1,1,0,0],
              [1,1,1,0,1],
              [1,1,1,1,0],
              [1,1,1,1,1]]
    return listas[aleatorio]

def simulated_annealing(temperatura = 1000, speed = 0.045, current=[1,0,0,1,1], best = current):
    while temperatura > 1:
        new = generarListaAleatoria()
        new_energy = energia(new)
        current_energy = energia(current)
        
        if funcion_aceptacion(new_energy, current_energy, temperatura):
            current = new
        
        if energia(new) > energia(best):
            best = new
            print(energia(best))
        
        temperatura *= 1 - speed

simulated_annealing()
