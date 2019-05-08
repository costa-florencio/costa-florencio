# costa-florencio
cadastro de pessoas
package projeto;

import javax.swing.JOptionPane;

public class Cadastro {
	static final int QTREGISTROS = 2;

	public static String codigo[] = new String[QTREGISTROS];
	public static String nome  [] = new String[QTREGISTROS];
	public static String email [] = new String[QTREGISTROS];
	public static String cidade[] = new String[QTREGISTROS];
	public static String uf    [] = new String[QTREGISTROS];

public static void main(String args[]) {
			String opcao = "";

		do {
		try {	
			opcao = JOptionPane.showInputDialog("Informe a sua opção: "
		+ "\n 1 - Cadastrar"
		+ "\n 2 - Consultar"
		+ "\n 3 - Atualizar"
		+ "\n 4 - Excluir"
		+ "\n 5 - Listar"
		+ "\n 6 - Sair");

		switch (Byte.parseByte(opcao)) {
			case 1: cadastrar();
				break; 
			case 2: consultar();
				break;
			case 3: atualizar();
				break;
			case 4: excluir();
				break;
			case 5: listar();
				break;
			case 6: sair();
				break;
			default: menssagem("Opcao inválida!");
				break;
			}
		}
	catch(NumberFormatException ex) {
		menssagem("Entrada de dados invalida !");}
	catch(Exception ex) {
		menssagem("Erro de Processamento.");}

		}while(opcao != "6");

	}

	private static void cadastrar() {
		int code = 1;
		for(int i=0; i<QTREGISTROS; i++) {
			codigo[i] = String.valueOf(code++);
			
			do {
			nome[i]= JOptionPane.showInputDialog("Digite seu nome:");
			}while(nome.length == 0);
			
			do {
			email[i]= JOptionPane.showInputDialog("Digite o E-mail:");
			}while(email.length == 0);
			
			cidade[i]= JOptionPane.showInputDialog("Digite a Cidade:");
			uf[i]= JOptionPane.showInputDialog("Digite a UF:");
			menssagem("Seu codigo é " + codigo[i] );
			}
	}
	private static void consultar() {
		int code = 0;
		code = Integer.parseInt(JOptionPane.showInputDialog("Informe o Codigo: "));
		menssagem("Nome: " + nome[code-1]+
				"\n E-mail: " + email[code-1]+
				"\n Cidade: " + cidade[code-1]+
				"\n UF: " + uf[code-1]);		
		}

	private static void atualizar() {
		int code = 0;
		code = Integer.parseInt(JOptionPane.showInputDialog("Informe o Codigo: "));
		
		do {
		nome   [code-1] = JOptionPane.showInputDialog("Digite o nome:");
		}while(nome.length == 0);
		
		do {
		email  [code-1] = JOptionPane.showInputDialog("Digite o E-mail:");
		}while(email.length == 0);
		
		cidade [code-1] = JOptionPane.showInputDialog("Digite a Cidade:");
		uf     [code-1] 
				= JOptionPane.showInputDialog("Informe sua Uf :");
		menssagem("Cadastro atualizado !");
		}

	private static void excluir() {
		int code = 0;
		code = Integer.parseInt(JOptionPane.showInputDialog("Informe o Codigo: "));
			nome   [code-1] = "vazio";
			email  [code-1] = "vazio";
			cidade [code-1] = "vazio";
			uf     [code-1] = "vazio";
		}

	private static void listar() {
		for(int i=0; i<QTREGISTROS; i++) {
			menssagem("\n Nome: " + nome[i] +
					"\n E-mail: " + email[i] +
					"\n Cidade: " + cidade[i] +
					"\n UF: " + uf[i]);
		}
	}

	private static void sair() {
		System.exit(0);
		}

	public static void menssagem(String texto) {
		JOptionPane.showMessageDialog(null, texto);
		}
	} 
