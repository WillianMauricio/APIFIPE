APIFIPE

    package Console;

    import java.util.ArrayList;
    import java.util.List;
    import java.util.Scanner;

    import Biblioteca.Uteis;
    import Classes.*;

    public class MainConsole {

      public static void main(String[] args) {
        Scanner read = new Scanner(System.in);
        List<Marca> listaMarca = new ArrayList<Marca>();
        Uteis util = new Uteis();
        List<Modelo> listaModelo = new ArrayList<Modelo>();
        List<AnoModelo> listaAnoModelo = new ArrayList<AnoModelo>();
        Carro carro = new Carro();
        Marca marca = new Marca();
        AnoModelo anoModelo = new AnoModelo();
        Modelo modelo = new Modelo();
        String local;

        System.out.println("1 - Buscar Marcas");
        System.out.println("2 - Buscar Modelos");
        System.out.println("3 - Buscar Ano/Modelo");
        System.out.println("4 - Buscar Carro");
        System.out.println("5 - Limpar Marcas");
        System.out.println("6 - Limpar Modelos");
        System.out.println("7 - Gerar JSON Marcas");
        System.out.println("8 - Gerar JSON Modelos");
        System.out.println("0 - Sair\n");
        int opcao = 1;
        if (util.testaConexao()) {
          System.out.println("Conexão Realizada!");
          while (opcao != 0) {
            opcao = read.nextInt();
            switch (opcao) {

            case 1:
              util = new Uteis();
              listaMarca = util.buscarMarcas();
              System.out.println(listaMarca.toString());
              marca = listaMarca.get(0);
              break;

            case 2:
              util = new Uteis();
              listaModelo = util.buscarModelos(marca);
              System.out.println(listaModelo.toString());
              modelo = listaModelo.get(0);
              break;
            case 3:
              util = new Uteis();
              listaAnoModelo = util.buscarAnoModelo(marca, modelo);
              System.out.println(listaAnoModelo.toString());
              anoModelo = listaAnoModelo.get(0);
              break;
            case 4:
              util = new Uteis();
              carro = util.buscarCarro(marca, modelo, anoModelo);
              System.out.println(carro.toString());
              break;
            case 5:
              util = new Uteis();
              listaMarca = util.limparMarca();
              System.out.println(listaMarca);
              break;
            case 6:
              util = new Uteis();
              listaModelo = util.limparModelo();
              System.out.println(listaModelo);
              break;
            case 7:
              util = new Uteis();
              local = "C:\\Users\\willi\\OneDrive\\Documentos\\BCC\\marcas";
              util.exportaMarca(local);
              break;
            case 8:
              util = new Uteis();
              local = "C:\\Users\\willi\\OneDrive\\Documentos\\BCC\\modelos";
              util.exportaModelo(local);
              break;
            case 0:
              System.out.println("Programa Finalizado");
              break;
            default:
              System.out.println("Opção Inválida!");
            }
          }
        } else { System.out.println("Erro na Conexãos!");}
        read.close();
      }
    }
