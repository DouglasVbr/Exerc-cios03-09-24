# Exerc-cios03-09-24

# Sistema de Gerenciamento de Estoque:



#PAGINA MAIN PARA TODOS OS EXERCICIOS 

#EXERCICCIO 1 
package exercícios;

public class Exercícios {

    
    public static void main(String[] args) {
        
        // cria produtos 
        produtos produtos1 = new produtos("PRODUTO A", 10.0, 5);
        produtos produtos2 = new produtos("produto b", 20.0, 2);
        
        
        //criar fornecedores 
        
        Fornecedores fornecedores1 = new Fornecedores("Fornecedor 1");
        
        
        //criar pedido 
        
        Pedidos pedidos = new Pedidos(fornecedores1);
        pedidos.adicionarProdutos(produtos1, 10);
        pedidos.adicionarProdutos(produtos2, 5);
        
        //exibir pedido 
        
        System.out.println(pedidos);
        
        
        //processar pedidos 
        pedidos.ProcessarPedido();
        
        
        //exibir estado dos produtos após o pedidos
        System.out.println(produtos1);
        System.out.println(produtos2);
        
        // Adiciona produto ao estoque 
        produtos1.adicionarEstoque(5);
        
        //remover produtos do estoque 
        produtos1.removeEstoque(3);
        
        
        //Verifica produtos com estoque baixo 
        
       if (produtos1.getQuantidade() < 5){
           System.out.println("Estoque abaixo para : " + produtos1.getNome() );
       }


       // 2.Sistema de Gerenciamento de Funcionários
        // Criando departamentos
        Departamento departamentoTI = new Departamento("TI");
        Departamento departamentoRH = new Departamento("RH");

        // Criando funcionários
        Funcionario funcionario1 = new Funcionario("Douglas", 3000);
        Funcionario funcionario2 = new Funcionario("Joel", 4000);
        Funcionario funcionario3 = new Funcionario("Alice", 3500);

        // Atribuindo funcionários aos departamentos
        departamentoTI.adicionarFuncionario(funcionario1);
        departamentoTI.adicionarFuncionario(funcionario2);
        departamentoRH.adicionarFuncionario(funcionario3);

        // Criando projetos
        Projeto projetoA = new Projeto("Projeto A");
        Projeto projetoB = new Projeto("Projeto B");

        // Atribuindo funcionários aos projetos
        projetoA.adicionarFuncionario(funcionario1);
        projetoB.adicionarFuncionario(funcionario2);
        projetoB.adicionarFuncionario(funcionario3);

        // Exibindo a média salarial do departamento TI
        System.out.println("Média salarial do departamento TI: " + departamentoTI.calcularMediaSalarial());

        // Exibindo projetos dos funcionários
        System.out.println("Projetos do funcionário Douglas: " + funcionario1.getProjeto().getNome());
        System.out.println("Projetos do funcionário Joel: " + funcionario2.getProjeto().getNome());
        System.out.println("Projetos do funcionário Alice: " + funcionario3.getProjeto().getNome());

        // 3. Aplicativo de Mídia Social
        // Criando usuários
        Usuario usuario1 = new Usuario("Alice");
        Usuario usuario2 = new Usuario("Bob");

        // Usuário 1 cria uma publicação
        usuario1.criarPublicacao("Olá, este é meu primeiro post!");
        usuario1.criarPublicacao("Acabei de fazer uma caminhada incrível!");

        // Usuário 2 cria uma publicação
        usuario2.criarPublicacao("Bom dia a todos!");

        // Usuário 2 comenta na publicação de Alice
        Publicacao publicacao1 = usuario1.getPublicacoes().get(0);
        publicacao1.adicionarComentario(usuario2, "Bem-vinda à plataforma, Alice!");

        // Listando as publicações de Alice
        usuario1.listarPublicacoes();

        // Listando os comentários na primeira publicação de Alice
        publicacao1.listarComentarios();

        // Listando as publicações de Bob
        usuario2.listarPublicacoes();

        // 4. Sistema de Reservas de Passagens
        // Criando passageiros
        Passageiro passageiro1 = new Passageiro("Carlos");
        Passageiro passageiro2 = new Passageiro("Ana");

        // Criando voos
        Voo voo1 = new Voo("ABC123", "São Paulo", 2);
        Voo voo2 = new Voo("XYZ789", "Rio de Janeiro", 1);

        // Fazendo reservas
        Reserva reserva1 = new Reserva(passageiro1, voo1);
        if (voo1.temDisponibilidade()) {
            voo1.adicionarReserva(reserva1);
            passageiro1.adicionarReserva(reserva1);
        }

        Reserva reserva2 = new Reserva(passageiro2, voo1);
        if (voo1.temDisponibilidade()) {
            voo1.adicionarReserva(reserva2);
            passageiro2.adicionarReserva(reserva2);
        }

        // Tentativa de reserva em voo lotado
        Reserva reserva3 = new Reserva(passageiro1, voo2);
        if (voo2.temDisponibilidade()) {
            voo2.adicionarReserva(reserva3);
            passageiro1.adicionarReserva(reserva3);
        } else {
            System.out.println("Não foi possível reservar o voo " + voo2.getNumero() + " para " + passageiro1.getNome() + ": voo lotado.");
        }

        // Listando as reservas de Carlos
        passageiro1.listarReservas();

        // Listando as reservas de Ana
        passageiro2.listarReservas();

        // 5. Sistema de Gerenciamento de Clínica
        // Criando médicos
        Medico medico1 = new Medico("Dr. João", "Cardiologista");
        Medico medico2 = new Medico("Dra. Ana", "Dermatologista");

        // Criando pacientes
        Paciente paciente1 = new Paciente("Carlos Silva", "123.456.789-00");
        Paciente paciente2 = new Paciente("Maria Oliveira", "987.654.321-00");

        // Agendando consultas
        Consulta consulta1 = new Consulta(paciente1, medico1, new Date());
        medico1.agendarConsulta(consulta1);

        Consulta consulta2 = new Consulta(paciente2, medico2, new Date());
        medico2.agendarConsulta(consulta2);

        Consulta consulta3 = new Consulta(paciente1, medico2, new Date());
        medico2.agendarConsulta(consulta3);

        // Listando pacientes de um médico
        medico1.listarPacientes();
        medico2.listarPacientes();

        // Exibindo próximas consultas de um médico
        medico1.exibirProximasConsultas();
        medico2.exibirProximasConsultas();

        // 6. Sistema de Gerenciamento de Carros
        // Criando marcas
        Marca marcaToyota = new Marca("Toyota");
        Marca marcaHonda = new Marca("Honda");

        // Criando carros
        Carro carro1 = new Carro("Corolla", 90000, marcaToyota);
        Carro carro2 = new Carro("Civic", 100000, marcaHonda);
        Carro carro3 = new Carro("Hilux", 150000, marcaToyota);

        // Adicionando carros às marcas
        marcaToyota.adicionarCarro(carro1);
        marcaToyota.adicionarCarro(carro3);
        marcaHonda.adicionarCarro(carro2);

        // Criando vendedores
        Vendedor vendedor1 = new Vendedor("Pedro");
        Vendedor vendedor2 = new Vendedor("Joana");

        // Vendendo carros
        vendedor1.venderCarro(carro1);
        vendedor2.venderCarro(carro2);
        vendedor1.venderCarro(carro3);

        // Calculando média de preços por marca
        System.out.println("Média de preços da Toyota: " + marcaToyota.calcularMediaPreco());
        System.out.println("Média de preços da Honda: " + marcaHonda.calcularMediaPreco());

        // Listando carros vendidos por cada vendedor
        vendedor1.listarCarrosVendidos();
        vendedor2.listarCarrosVendidos();

        // 7. Sistema de Biblioteca Virtual Avançada
        // Criando autores
        Autor autor1 = new Autor("George Orwell");
        Autor autor2 = new Autor("J.K. Rowling");

        // Criando livros
        Livro livro1 = new Livro("1984", autor1, 5);
        Livro livro2 = new Livro("Harry Potter e a Pedra Filosofal", autor2, 3);

        // Criando usuários
        usuario1 = new Usuario("Alice");
        usuario2 = new Usuario("Bob");

        // Realizando empréstimos
        Emprestimo emprestimo1 = new Emprestimo(livro1, usuario1, new Date());
        usuario1.adicionarEmprestimo(emprestimo1);
        livro1.diminuirQuantidadeDisponivel();
        livro1.incrementarVezesEmprestado();

        Emprestimo emprestimo2 = new Emprestimo(livro2, usuario2, new Date());
        usuario2.adicionarEmprestimo(emprestimo2);
        livro2.diminuirQuantidadeDisponivel();
        livro2.incrementarVezesEmprestado();

        // Devolvendo livro (caso já tenha passado do prazo)
        emprestimo1.devolver();
        double multa = emprestimo1.calcularMulta();
        if (multa > 0) {
            System.out.println("Multa para o empréstimo do livro " + emprestimo1.getLivro().getTitulo() + ": R$ " + multa);
        }

        // Listando empréstimos de um usuário
        usuario1.listarEmprestimos();
        usuario2.listarEmprestimos();

        // Calculando os livros mais populares
        ArrayList<Livro> livros = new ArrayList<>();
        livros.add(livro1);
        livros.add(livro2);

        System.out.println("Livros mais populares:");
        livros.stream()
                .sorted((l1, l2) -> Integer.compare(l2.getVezesEmprestado(), l1.getVezesEmprestado()))
                .forEach(livro -> System.out.println("- " + livro.getTitulo() + " (Emprestado " + livro.getVezesEmprestado() + " vezes)"));
        
        
        // 8. Sistema de Gerenciamento de Projetos
        
         // Criando desenvolvedores
        Desenvolvedor dev1 = new Desenvolvedor("Alice");
        Desenvolvedor dev2 = new Desenvolvedor("Bob");

        // Criando projetos
        Projeto projeto1 = new Projeto("Sistema de Vendas");
        Projeto projeto2 = new Projeto("Aplicativo Mobile");

        // Criando tarefas
        Tarefa tarefa1 = new Tarefa("Implementar frontend", 20);
        Tarefa tarefa2 = new Tarefa("Desenvolver backend", 40);
        Tarefa tarefa3 = new Tarefa("Testar aplicação", 15);

        // Atribuindo tarefas aos projetos
        projeto1.adicionarTarefa(tarefa1);
        projeto1.adicionarTarefa(tarefa2);
        projeto2.adicionarTarefa(tarefa3);

        // Atribuindo tarefas aos desenvolvedores
        dev1.adicionarTarefa(tarefa1);
        dev2.adicionarTarefa(tarefa2);
        dev1.adicionarTarefa(tarefa3);

        // Calculando a carga de trabalho dos projetos
        System.out.println("Carga de trabalho do projeto " + projeto1.getNome() + ": " + projeto1.calcularCargaDeTrabalho() + " horas");
        System.out.println("Carga de trabalho do projeto " + projeto2.getNome() + ": " + projeto2.calcularCargaDeTrabalho() + " horas");

        // Listando tarefas de cada desenvolvedor
        dev1.listarTarefas();
        dev2.listarTarefas();
        
        
        // 9. Sistema de Gerenciamento de Restaurantes
        
         // Criando pratos
        Prato prato1 = new Prato("Spaghetti Carbonara", 25.0);
        Prato prato2 = new Prato("Bife à Parmegiana", 30.0);
        Prato prato3 = new Prato("Salada Caesar", 15.0);

        // Criando mesas
        Mesa mesa1 = new Mesa(1);
        Mesa mesa2 = new Mesa(2);

        // Criando pedidos
        Pedido pedido1 = new Pedido(mesa1);
        pedido1.adicionarPrato(prato1);
        pedido1.adicionarPrato(prato3);
        mesa1.adicionarPedido(pedido1);

        Pedido pedido2 = new Pedido(mesa2);
        pedido2.adicionarPrato(prato2);
        mesa2.adicionarPedido(pedido2);

        // Exibindo pedidos e total da conta
        pedido1.exibirPedido();
        pedido2.exibirPedido();

        // Reservando mesas
        mesa1.reservarMesa(new Date(2024, 9, 10)); // Reservando a mesa 1 para o dia 10/09/2024
        mesa2.reservarMesa(new Date(2024, 9, 11)); // Reservando a mesa 2 para o dia 11/09/2024

        // Exibindo reservas futuras
        mesa1.exibirReservas();
        mesa2.exibirReservas();
        
        // 10. Sistema de Gerenciamento de Estudantes
        
         // Criando professores
        Professor professor1 = new Professor("Dr. João");
        Professor professor2 = new Professor("Dra. Maria");

        // Criando disciplinas
        Disciplina disciplina1 = new Disciplina("Matemática", professor1);
        Disciplina disciplina2 = new Disciplina("Física", professor2);
        Disciplina disciplina3 = new Disciplina("Química", professor1);

        // Criando estudantes
        Estudante estudante1 = new Estudante("Ana");
        Estudante estudante2 = new Estudante("Bruno");

        // Matriculando estudantes nas disciplinas
        disciplina1.matricularEstudante(estudante1);
        disciplina1.matricularEstudante(estudante2);
        disciplina2.matricularEstudante(estudante1);
        disciplina3.matricularEstudante(estudante2);

        // Adicionando notas aos estudantes
        estudante1.adicionarNota(disciplina1, 8.5);
        estudante1.adicionarNota(disciplina2, 7.0);
        estudante2.adicionarNota(disciplina1, 9.0);
        estudante2.adicionarNota(disciplina3, 6.5);

        // Calculando e exibindo a média de cada estudante
        System.out.println("Média de " + estudante1.getNome() + ": " + estudante1.calcularMedia());
        System.out.println("Média de " + estudante2.getNome() + ": " + estudante2.calcularMedia());

        // Listando disciplinas de cada professor
        professor1.listarDisciplinas();
        professor2.listarDisciplinas();

        // Listando disciplinas de cada estudante
        estudante1.listarDisciplinas();
        estudante2.listarDisciplinas();
    }
    
}



# CLASS PRODUTOS 


package exercícios;


public class produtos {
    
    private String nome ;
    private double preco;
    private int quantidade;
    
    
    public produtos(String nome, double preco, int quantidade){
    this.nome = nome;
    this.preco = preco;
    this.quantidade = quantidade;
    }

    public String getNome() {
        return nome;
    }

    public double getPreco() {
        return preco;
    }

    public int getQuantidade() {
        return quantidade;
    }
    
    public void adicionarEstoque(int quantidade){
    this.quantidade+= quantidade;
    
    }
    
    public void removeEstoque(int quantidade){
    
        if(this.quantidade >= quantidade){
            this.quantidade-=quantidade;
        }else{
            System.out.println("Estoque insuficiente para " + nome);
        }
    }
    
    @Override
    public String toString(){
        return String.format("Produtos{name='%s', preco=%.2f, quantidades=%d}", nome, preco, quantidade);
    
    }
}

# CLASS FORNECEDORES 


package exercícios;


public class Fornecedores {
    
    private String nome;
    
    public Fornecedores (String nome){
    this.nome = nome;
            }
    public String getNome(){
    
        return nome;
    }
    
}


# CLASS PEDIDOS 


package exercícios;

import java.util.HashMap;
import java.util.Map;

public class Pedidos {
    
    
    private Fornecedores fornecedores;
    private Map<produtos, Integer> produtosPedidos;
    
    
    public Pedidos(Fornecedores fornecedores){
    this.fornecedores = fornecedores;
    this.produtosPedidos = new HashMap<>();
    
    }
    
    public void adicionarProdutos(produtos Produtos, int quantidade){
    
        produtosPedidos.put(Produtos, quantidade);
    }
    
    public void ProcessarPedido(){
     
        for (Map.Entry<produtos, Integer> entry : produtosPedidos.entrySet()) {
        
            produtos Produtos = entry.getKey();
            int quantidade = entry.getValue();
            Produtos.adicionarEstoque(quantidade);
        }
    
    }
    
    
    @Override
    public String toString(){
    
    StringBuilder sb = new StringBuilder();
    sb.append("Pedido para o fornecedor ").append(fornecedores.getNome()).append("\n");
     for (Map.Entry< produtos, Integer> entry : produtosPedidos.entrySet()) {
        sb.append(entry.getKey().getNome()).append(":").append(entry.getValue()).append("\n");
     }  
     return sb.toString();
    }
}



package exercícios;

/**
 *
 * @author Douglas
 */
public class Funcionario {
    
    private String nome;
    private double salario;
    private Departamento departamento;
    private Projeto projeto;

    public Funcionario(String nome, double salario) {
        this.nome = nome;
        this.salario = salario;
    }

    public String getNome() {
        return nome;
    }

    public double getSalario() {
        return salario;
    }

    public Departamento getDepartamento() {
        return departamento;
    }

    public Projeto getProjeto() {
        return projeto;
    }

    public void setDepartamento(Departamento departamento) {
        this.departamento = departamento;
    }

    public void setProjeto(Projeto projeto) {
        this.projeto = projeto;
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Departamento {
    
    private String nome;
    private ArrayList<Funcionario> funcionarios;

    public Departamento(String nome) {
        this.nome = nome;
        this.funcionarios = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Funcionario> getFuncionarios() {
        return funcionarios;
    }

    public void adicionarFuncionario(Funcionario funcionario) {
        funcionarios.add(funcionario);
        funcionario.setDepartamento(this);
    }

    public double calcularMediaSalarial() {
        if (funcionarios.isEmpty()) {
            return 0;
        }
        double somaSalarios = 0;
        for (Funcionario funcionario : funcionarios) {
            somaSalarios += funcionario.getSalario();
        }
        return somaSalarios / funcionarios.size();
    }
    
    
    
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Projeto {
    
     private String nome;
    private ArrayList<Funcionario> funcionarios;
     private ArrayList<Tarefa> tarefas;

    public Projeto(String nome) {
        this.nome = nome;
        this.funcionarios = new ArrayList<>();
        this.tarefas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }
    
     public ArrayList<Tarefa> getTarefas() {
        return tarefas;
    }
     
     public void adicionarTarefa(Tarefa tarefa) {
        tarefas.add(tarefa);
    }

    public ArrayList<Funcionario> getFuncionarios() {
        return funcionarios;
    }

    public void adicionarFuncionario(Funcionario funcionario) {
        funcionarios.add(funcionario);
        funcionario.setProjeto(this);
    }
    
    public int calcularCargaDeTrabalho() {
        int cargaTotal = 0;
        for (Tarefa tarefa : tarefas) {
            cargaTotal += tarefa.getHorasEstimadas();
        }
        return cargaTotal;
    }
}


package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Usuario {

    private String nome;
    private ArrayList<Publicacao> publicacoes;
    private ArrayList<Emprestimo> emprestimos;

    public Usuario(String nome) {
        this.nome = nome;
        this.publicacoes = new ArrayList<>();
        this.emprestimos = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Publicacao> getPublicacoes() {
        return publicacoes;
    }
    
     public ArrayList<Emprestimo> getEmprestimos() {
        return emprestimos;
    }
     
      public void adicionarEmprestimo(Emprestimo emprestimo) {
        emprestimos.add(emprestimo);
    }

    public void criarPublicacao(String conteudo) {
        Publicacao novaPublicacao = new Publicacao(this, conteudo);
        publicacoes.add(novaPublicacao);
    }
    
    public void listarEmprestimos() {
        System.out.println("Empréstimos de " + nome + ":");
        for (Emprestimo emprestimo : emprestimos) {
            System.out.println("- " + emprestimo.getLivro().getTitulo() + " (Data de Empréstimo: " + emprestimo.getDataEmprestimo() + ")");
        }
    }

    public void listarPublicacoes() {
        System.out.println("Publicações de " + nome + ":");
        for (Publicacao publicacao : publicacoes) {
            System.out.println("- " + publicacao.getConteudo());
        }
    }

   

}
 
package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Publicacao {
    
     private Usuario autor;
    private String conteudo;
    private ArrayList<Comentario> comentarios;

    public Publicacao(Usuario autor, String conteudo) {
        this.autor = autor;
        this.conteudo = conteudo;
        this.comentarios = new ArrayList<>();
    }

    public Usuario getAutor() {
        return autor;
    }

    public String getConteudo() {
        return conteudo;
    }

    public ArrayList<Comentario> getComentarios() {
        return comentarios;
    }

    public void adicionarComentario(Usuario autor, String conteudo) {
        Comentario novoComentario = new Comentario(autor, conteudo);
        comentarios.add(novoComentario);
    }

    public void listarComentarios() {
        System.out.println("Comentários na publicação \"" + conteudo + "\":");
        for (Comentario comentario : comentarios) {
            System.out.println("- " + comentario.getAutor().getNome() + ": " + comentario.getConteudo());
        }
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Comentario {
    
     private Usuario autor;
    private String conteudo;

    public Comentario(Usuario autor, String conteudo) {
        this.autor = autor;
        this.conteudo = conteudo;
    }

    public Usuario getAutor() {
        return autor;
    }

    public String getConteudo() {
        return conteudo;
    }
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Passageiro {
    
       private String nome;
    private ArrayList<Reserva> reservas;

    public Passageiro(String nome) {
        this.nome = nome;
        this.reservas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Reserva> getReservas() {
        return reservas;
    }

    public void adicionarReserva(Reserva reserva) {
        reservas.add(reserva);
    }

    public void listarReservas() {
        System.out.println("Reservas de " + nome + ":");
        for (Reserva reserva : reservas) {
            System.out.println("- Voo " + reserva.getVoo().getNumero() + " para " + reserva.getVoo().getDestino());
        }
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Voo {
    
     private String numero;
    private String destino;
    private int capacidade;
    private ArrayList<Reserva> reservas;

    public Voo(String numero, String destino, int capacidade) {
        this.numero = numero;
        this.destino = destino;
        this.capacidade = capacidade;
        this.reservas = new ArrayList<>();
    }

    public String getNumero() {
        return numero;
    }

    public String getDestino() {
        return destino;
    }

    public int getCapacidade() {
        return capacidade;
    }

    public ArrayList<Reserva> getReservas() {
        return reservas;
    }

    public boolean temDisponibilidade() {
        return reservas.size() < capacidade;
    }

    public void adicionarReserva(Reserva reserva) {
        if (temDisponibilidade()) {
            reservas.add(reserva);
        } else {
            System.out.println("Voo " + numero + " está lotado.");
        }
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Reserva {
    
    private Passageiro passageiro;
    private Voo voo;

    public Reserva(Passageiro passageiro, Voo voo) {
        this.passageiro = passageiro;
        this.voo = voo;
    }

    public Passageiro getPassageiro() {
        return passageiro;
    }

    public Voo getVoo() {
        return voo;
    }
    
}
 
package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Medico {
    
     private String nome;
    private String especialidade;
    private ArrayList<Consulta> consultas;

    public Medico(String nome, String especialidade) {
        this.nome = nome;
        this.especialidade = especialidade;
        this.consultas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public String getEspecialidade() {
        return especialidade;
    }

    public ArrayList<Consulta> getConsultas() {
        return consultas;
    }

    public void agendarConsulta(Consulta consulta) {
        consultas.add(consulta);
    }

    public void listarPacientes() {
        System.out.println("Pacientes do Dr. " + nome + ":");
        for (Consulta consulta : consultas) {
            System.out.println("- " + consulta.getPaciente().getNome());
        }
    }

    public void exibirProximasConsultas() {
        System.out.println("Próximas consultas do Dr. " + nome + ":");
        for (Consulta consulta : consultas) {
            System.out.println("- Paciente: " + consulta.getPaciente().getNome() + " | Data: " + consulta.getData());
        }
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Paciente {
    
    private String nome;
    private String cpf;

    public Paciente(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }

    public String getNome() {
        return nome;
    }

    public String getCpf() {
        return cpf;
    }
}

package exercícios;

import java.util.Date;

/**
 *
 * @author Douglas
 */
public class Consulta {
    
     private Paciente paciente;
    private Medico medico;
    private Date data;

    public Consulta(Paciente paciente, Medico medico, Date data) {
        this.paciente = paciente;
        this.medico = medico;
        this.data = data;
    }

    public Paciente getPaciente() {
        return paciente;
    }

    public Medico getMedico() {
        return medico;
    }

    public Date getData() {
        return data;
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Carro {
    private String modelo;
    private double preco;
    private Marca marca;
    private boolean vendido;

    public Carro(String modelo, double preco, Marca marca) {
        this.modelo = modelo;
        this.preco = preco;
        this.marca = marca;
        this.vendido = false;
    }

    public String getModelo() {
        return modelo;
    }

    public double getPreco() {
        return preco;
    }

    public Marca getMarca() {
        return marca;
    }

    public boolean isVendido() {
        return vendido;
    }

    public void vender() {
        this.vendido = true;
    }
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Marca {
    
     private String nome;
    private ArrayList<Carro> carros;

    public Marca(String nome) {
        this.nome = nome;
        this.carros = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Carro> getCarros() {
        return carros;
    }

    public void adicionarCarro(Carro carro) {
        carros.add(carro);
    }

    public double calcularMediaPreco() {
        if (carros.isEmpty()) {
            return 0;
        }
        double somaPrecos = 0;
        for (Carro carro : carros) {
            somaPrecos += carro.getPreco();
        }
        return somaPrecos / carros.size();
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Vendedor {
    
    private String nome;
    private ArrayList<Carro> carrosVendidos;

    public Vendedor(String nome) {
        this.nome = nome;
        this.carrosVendidos = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public void venderCarro(Carro carro) {
        if (!carro.isVendido()) {
            carro.vender();
            carrosVendidos.add(carro);
        } else {
            System.out.println("O carro já foi vendido.");
        }
    }

    public void listarCarrosVendidos() {
        System.out.println("Carros vendidos por " + nome + ":");
        for (Carro carro : carrosVendidos) {
            System.out.println("- " + carro.getModelo() + " (" + carro.getMarca().getNome() + ")");
        }
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Livro {
    
    private String titulo;
    private Autor autor;
    private int quantidadeDisponivel;
    private int vezesEmprestado;

    public Livro(String titulo, Autor autor, int quantidadeDisponivel) {
        this.titulo = titulo;
        this.autor = autor;
        this.quantidadeDisponivel = quantidadeDisponivel;
        this.vezesEmprestado = 0;
    }

    public String getTitulo() {
        return titulo;
    }

    public Autor getAutor() {
        return autor;
    }

    public int getQuantidadeDisponivel() {
        return quantidadeDisponivel;
    }

    public void diminuirQuantidadeDisponivel() {
        if (quantidadeDisponivel > 0) {
            quantidadeDisponivel--;
        }
    }

    public void aumentarQuantidadeDisponivel() {
        quantidadeDisponivel++;
    }

    public void incrementarVezesEmprestado() {
        vezesEmprestado++;
    }

    public int getVezesEmprestado() {
        return vezesEmprestado;
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Autor {
    private String nome;

    public Autor(String nome) {
        this.nome = nome;
    }

    public String getNome() {
        return nome;
    }
    
}
package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Usuario {

    private String nome;
    private ArrayList<Publicacao> publicacoes;
    private ArrayList<Emprestimo> emprestimos;

    public Usuario(String nome) {
        this.nome = nome;
        this.publicacoes = new ArrayList<>();
        this.emprestimos = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Publicacao> getPublicacoes() {
        return publicacoes;
    }
    
     public ArrayList<Emprestimo> getEmprestimos() {
        return emprestimos;
    }
     
      public void adicionarEmprestimo(Emprestimo emprestimo) {
        emprestimos.add(emprestimo);
    }

    public void criarPublicacao(String conteudo) {
        Publicacao novaPublicacao = new Publicacao(this, conteudo);
        publicacoes.add(novaPublicacao);
    }
    
    public void listarEmprestimos() {
        System.out.println("Empréstimos de " + nome + ":");
        for (Emprestimo emprestimo : emprestimos) {
            System.out.println("- " + emprestimo.getLivro().getTitulo() + " (Data de Empréstimo: " + emprestimo.getDataEmprestimo() + ")");
        }
    }

    public void listarPublicacoes() {
        System.out.println("Publicações de " + nome + ":");
        for (Publicacao publicacao : publicacoes) {
            System.out.println("- " + publicacao.getConteudo());
        }
    }

   

}

package exercícios;

import java.util.Date;

/**
 *
 * @author Douglas
 */
public class Emprestimo {
     private Livro livro;
    private Usuario usuario;
    private Date dataEmprestimo;
    private Date dataDevolucao;
    private boolean devolvido;
    private static final long DIAS_PARA_DEVOLUCAO = 14;
    private static final double MULTA_POR_DIA = 2.0;

    public Emprestimo(Livro livro, Usuario usuario, Date dataEmprestimo) {
        this.livro = livro;
        this.usuario = usuario;
        this.dataEmprestimo = dataEmprestimo;
        this.dataDevolucao = new Date(dataEmprestimo.getTime() + (DIAS_PARA_DEVOLUCAO * 24 * 60 * 60 * 1000L));
        this.devolvido = false;
    }

    public Livro getLivro() {
        return livro;
    }

    public Usuario getUsuario() {
        return usuario;
    }

    public Date getDataEmprestimo() {
        return dataEmprestimo;
    }

    public Date getDataDevolucao() {
        return dataDevolucao;
    }

    public void devolver() {
        if (!devolvido) {
            devolvido = true;
            livro.aumentarQuantidadeDisponivel();
        }
    }

    public boolean isDevolvido() {
        return devolvido;
    }

    public double calcularMulta() {
        if (!devolvido && new Date().after(dataDevolucao)) {
            long diasAtraso = (new Date().getTime() - dataDevolucao.getTime()) / (1000 * 60 * 60 * 24);
            return diasAtraso * MULTA_POR_DIA;
        }
        return 0;
    }
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Projeto {
    
     private String nome;
    private ArrayList<Funcionario> funcionarios;
     private ArrayList<Tarefa> tarefas;

    public Projeto(String nome) {
        this.nome = nome;
        this.funcionarios = new ArrayList<>();
        this.tarefas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }
    
     public ArrayList<Tarefa> getTarefas() {
        return tarefas;
    }
     
     public void adicionarTarefa(Tarefa tarefa) {
        tarefas.add(tarefa);
    }

    public ArrayList<Funcionario> getFuncionarios() {
        return funcionarios;
    }

    public void adicionarFuncionario(Funcionario funcionario) {
        funcionarios.add(funcionario);
        funcionario.setProjeto(this);
    }
    
    public int calcularCargaDeTrabalho() {
        int cargaTotal = 0;
        for (Tarefa tarefa : tarefas) {
            cargaTotal += tarefa.getHorasEstimadas();
        }
        return cargaTotal;
    }

    

    
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Desenvolvedor {
    private String nome;
    private ArrayList<Tarefa> tarefas;

    public Desenvolvedor(String nome) {
        this.nome = nome;
        this.tarefas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public ArrayList<Tarefa> getTarefas() {
        return tarefas;
    }

    public void adicionarTarefa(Tarefa tarefa) {
        tarefa.atribuirDesenvolvedor(this);
        tarefas.add(tarefa);
    }

    public void listarTarefas() {
        System.out.println("Tarefas atribuídas ao desenvolvedor " + nome + ":");
        for (Tarefa tarefa : tarefas) {
            System.out.println("- " + tarefa.getNome() + " (" + tarefa.getHorasEstimadas() + " horas)");
        }
    }
    
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Tarefa {
    
    private String nome;
    private int horasEstimadas;
    private Desenvolvedor desenvolvedor;

    public Tarefa(String nome, int horasEstimadas) {
        this.nome = nome;
        this.horasEstimadas = horasEstimadas;
        this.desenvolvedor = null;
    }

    public String getNome() {
        return nome;
    }

    public int getHorasEstimadas() {
        return horasEstimadas;
    }

    public Desenvolvedor getDesenvolvedor() {
        return desenvolvedor;
    }

    public void atribuirDesenvolvedor(Desenvolvedor desenvolvedor) {
        this.desenvolvedor = desenvolvedor;
    }


   
}

package exercícios;

/**
 *
 * @author Douglas
 */
public class Prato {
    private String nome;
    private double preco;

    public Prato(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }

    public String getNome() {
        return nome;
    }

    public double getPreco() {
        return preco;
    }
}

package exercícios;

import java.util.ArrayList;
import java.util.Date;

/**
 *
 * @author Douglas
 */
public class Mesa {
    
    private int numero;
    private ArrayList<Pedido> pedidos;
    private Date reserva;

    public Mesa(int numero) {
        this.numero = numero;
        this.pedidos = new ArrayList<>();
    }

    public int getNumero() {
        return numero;
    }

    public void adicionarPedido(Pedido pedido) {
        pedidos.add(pedido);
    }

    public void reservarMesa(Date dataReserva) {
        this.reserva = dataReserva;
    }

    public Date getReserva() {
        return reserva;
    }

    public void exibirReservas() {
        if (reserva != null) {
            System.out.println("Mesa " + numero + " reservada para " + reserva);
        } else {
            System.out.println("Mesa " + numero + " não está reservada.");
        }
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Pedido {
    private ArrayList<Prato> pratos;
    private Mesa mesa;

    public Pedido(Mesa mesa) {
        this.mesa = mesa;
        this.pratos = new ArrayList<>();
    }

    public void adicionarPrato(Prato prato) {
        pratos.add(prato);
    }

    public double calcularTotal() {
        double total = 0;
        for (Prato prato : pratos) {
            total += prato.getPreco();
        }
        return total;
    }

    public void exibirPedido() {
        System.out.println("Pedido da mesa " + mesa.getNumero() + ":");
        for (Prato prato : pratos) {
            System.out.println("- " + prato.getNome() + " : R$ " + prato.getPreco());
        }
        System.out.println("Total: R$ " + calcularTotal());
    }

    public Mesa getMesa() {
        return mesa;
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Estudante {
    private String nome;
    private ArrayList<Disciplina> disciplinas;
    private ArrayList<Double> notas;

    public Estudante(String nome) {
        this.nome = nome;
        this.disciplinas = new ArrayList<>();
        this.notas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public void matricularDisciplina(Disciplina disciplina) {
        disciplinas.add(disciplina);
    }

    public void adicionarNota(Disciplina disciplina, double nota) {
        int index = disciplinas.indexOf(disciplina);
        if (index != -1) {
            notas.add(index, nota);
        } else {
            System.out.println("O estudante não está matriculado nesta disciplina.");
        }
    }

    public double calcularMedia() {
        double soma = 0;
        for (double nota : notas) {
            soma += nota;
        }
        return notas.size() > 0 ? soma / notas.size() : 0;
    }

    public void listarDisciplinas() {
        System.out.println("Disciplinas de " + nome + ":");
        for (Disciplina disciplina : disciplinas) {
            System.out.println("- " + disciplina.getNome());
        }
    }
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Professor {
    
     private String nome;
    private ArrayList<Disciplina> disciplinas;

    public Professor(String nome) {
        this.nome = nome;
        this.disciplinas = new ArrayList<>();
    }

    public String getNome() {
        return nome;
    }

    public void adicionarDisciplina(Disciplina disciplina) {
        disciplinas.add(disciplina);
    }

    public void listarDisciplinas() {
        System.out.println("Disciplinas ministradas pelo professor " + nome + ":");
        for (Disciplina disciplina : disciplinas) {
            System.out.println("- " + disciplina.getNome());
        }
    }
    
}

package exercícios;

import java.util.ArrayList;

/**
 *
 * @author Douglas
 */
public class Disciplina {
    private String nome;
    private Professor professor;
    private ArrayList<Estudante> estudantes;

    public Disciplina(String nome, Professor professor) {
        this.nome = nome;
        this.professor = professor;
        this.estudantes = new ArrayList<>();
        professor.adicionarDisciplina(this);
    }

    public String getNome() {
        return nome;
    }

    public Professor getProfessor() {
        return professor;
    }

    public void matricularEstudante(Estudante estudante) {
        estudantes.add(estudante);
        estudante.matricularDisciplina(this);
    }

    public void listarEstudantes() {
        System.out.println("Estudantes matriculados em " + nome + ":");
        for (Estudante estudante : estudantes) {
            System.out.println("- " + estudante.getNome());
        }
    }
}







