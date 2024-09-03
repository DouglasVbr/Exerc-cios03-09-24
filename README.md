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





