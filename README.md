# dni
## Resultados posibles del dni en java
```java
import java.util.*;

public class dni {
	
	public static boolean ValidarDNI(String dni){
		dni = dni.replaceAll("\\s","").trim();
		boolean comprovarLletra;
		boolean comprovarNumero;
		int lletra = 0;
		int contaNumeros = 0;
		String cadNumeros = "";
		int numeros;
		int resto;
		boolean valid = false;
		char[] arr = {'T','R','W','A','G','M','Y','F','P','D','X','B','N','J','Z','S','Q','V','H','L','C','K','E'};
		dni = dni.toUpperCase();
		if(dni.length() == 9) {
			comprovarLletra = Character.isLetter(dni.charAt(8));
			if(comprovarLletra == false)
				System.out.println("El último caracter del dni tiene que ser una letra");
			else{
				lletra = dni.charAt(8);
				if(lletra >= 'A' && lletra <='Z')
					cadNumeros = dni.substring(0,8);
				for(int i = 0;i <= 7;i++){
					comprovarNumero = Character.isDigit(dni.charAt(i));
					if(comprovarNumero == true)
						contaNumeros++;
					else
						System.out.println("El caracter "+(i+1)+" no es un número");
				}
				if(contaNumeros == 8){
					numeros = Integer.valueOf(cadNumeros);
					resto = numeros%23;
					if(arr[resto] == lletra)
						valid = true;
					else
						System.out.println("La letra corresponiente al número"+numeros+" es "+arr[resto]);
				}
			}
		}else {
			valid=false;
		}
		return valid;
	}
	
	public static void main(String[] args) {
		Scanner lector = new Scanner (System.in);
		String dni;
		
		System.out.print("Escriu el DNI: ");
		dni=lector.nextLine();
		if(ValidarDNI(dni)==true) {
			System.out.println("El dni esta bien introducido");
		}else {
			System.out.println("El dni esta mal introducido");
		}
		
	}
}
```
