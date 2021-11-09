# Álgebra-Abstracta-Italo-Kancha-Vilca
Laboratorio 5

**NOMBRE:** Italo kancha vilca

**grupo:** Ccomp 3-1


 1.- Implementar un algoritmo para calcular x (el inverso multiplicativo de a, m´odulo n). El programa debe permitir ingresar el n´umero a y n, luego debe
retorna el valor de x (si es que existe).
 
 - ¿Cual es la inversa multiplicativa?
 
![image](https://user-images.githubusercontent.com/54363893/141001010-a29aa80e-f53b-43ef-b7dc-c4096e9a88a2.png)

EXPLICACIÓN DEL CODIGO CON COMENTARIOS:

```c ++
#include<iostream>
using namespace std;
class InverseModulo {
private:
	int mod(int a, int b) {
		int	c = a % b;
		return (c < 0) ? c + b : c;
	}

public:
	int euclides(int a, int b) {
		if (b == 0)
			return a;
		else
			return euclides(b, a % b);
	}
	int calculoInversa(int a, int b) {
		int n = a;
		int old_x = 1, x = 0;
		int old_y = 0, y = 1;
		int q, r;
		while (b != 0) {
			q = a / b;//Cociente 
			r = a % b;//resto
			int temp = x;
			x = old_x - q * x;
			old_x = temp;
			temp = y;
			y = old_y - q * y;
			old_y = temp;
			a = b;
			b = r;
		}
		int inverse = mod(old_y, n);
		return  inverse;
	}

};

int main() {
	InverseModulo obj;
	int a, n, i;
	cout << "		=== Calculo de la inversa multiplicativa  ===="<<endl<<endl;
	cout << "Ingresa un numero para hallar su inversa: "<<endl;
	cin >> a;
	cout << endl;
	cout << "Ingrese el modulo para el inverso " << a << "\n";
	cin >> n;
	cout << "------------RESPUESTA-------------"<<endl<<endl;

	if (obj.euclides(a, n) == 1) 
	{
		i = obj.calculoInversa(n, a);
		cout << "La inversa de " << a << " con modulo " << n << " es " << i << endl;
	}
	else 
	{
		cout << "La inversa de " << a << " con modulo " << n << " No existe" << endl;
	}

	return 0;
}
```
