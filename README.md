# Lotofacil2409
//Atividades de linguagem de programação - Newton.

package org.example;

import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Random;
import javax.swing.*;


    public class Lotofacil extends JFrame {

        private JPanel painel = new JPanel();
        private JButton Aposta1 = new JButton("Apostar de 0 a 100 ");
        private JButton Aposta2 = new JButton("Apostar de A a Z");
        private JButton Aposta3 = new JButton("Apostar par ou ímpar ");
        private JButton Sair = new JButton("Sair");
        private JLabel jLabelMensagem = new JLabel("Lotofácil");

        public Lotofacil (){
            this.setTitle ("Lotofácil");
            this.setSize (350,225 );
            painel.setLayout (new FlowLayout(FlowLayout.CENTER, 100, 10));
            painel.setBackground (new Color (255, 255, 255, 255));
            painel.add(jLabelMensagem);

            Aposta1.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {

                    String aposta = JOptionPane.showInputDialog(null, "Digite um número de 0 a 100.");
                    int numero = Integer.parseInt(aposta);
                    Random rnd = new Random();
                    int sorteio = rnd.nextInt(101);

                    if (sorteio == numero) {

                        JOptionPane.showMessageDialog (null, "Você acertou!");
                    }
                    else {
                        JOptionPane.showMessageDialog (null, "Você perdeu. O número correto é: " + sorteio);

                    }
                }
            });

            Aposta2.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    String aposta = JOptionPane.showInputDialog(null, "Digite uma letra de A a Z.");
                    Random random = new Random();
                    char letracorreta = (char) (random.nextInt(26) + 'a');
                    String letraCorretaString = String.valueOf(letracorreta);

                    if (aposta != null && aposta.length() == 1) {
                        aposta = aposta.toLowerCase();
                        if (aposta.equals(letraCorretaString)) {
                            JOptionPane.showMessageDialog(null, "Você acertou!");
                        } else {
                            JOptionPane.showMessageDialog(null, "Você errou. A letra correta é " + letraCorretaString);
                        }
                    } else {
                        JOptionPane.showMessageDialog(null, "Por favor, insira uma única letra de A a Z.");
                    }
                }
            });

            Aposta3.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    String aposta = JOptionPane.showInputDialog(null, "Digite um número.");
                    int numeroApostado = Integer.parseInt(aposta);
                    if (numeroApostado %2 == 0){
                        JOptionPane.showMessageDialog(null,"Número par! Você ganhou!");
                    }
                    else{
                        JOptionPane.showMessageDialog (null, "Não ganhou.");

                    }

                }
            });

            Sair.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    int resposta = JOptionPane.showConfirmDialog(null, "Deseja sair?", "Confirmar saída", JOptionPane.YES_NO_OPTION);
                    if (resposta == JOptionPane.YES_OPTION){
                        System.exit(0);
                    }
                }
            });


            painel.add (Aposta1);
            painel.add (Aposta2);
            painel.add (Aposta3);
            painel.add (Sair);

            this.getContentPane().add(painel);
            this.setLocationRelativeTo(null);
            this.setVisible(true);
            this.setDefaultCloseOperation(EXIT_ON_CLOSE);}

        public static void main(String[] args) {
            new Lotofacil();


        }


    }


