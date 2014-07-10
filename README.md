laboratorio1
============

radio


Interfaz:


    public interface InterfaceRadio {
      public void cambiarEstado(boolean estado);
      public void cambiarFrecuencia(boolean estado); /// am false fm true
      public void subirEstacion (double Estacion);
      public void bajarEstacion (double Estacion);
      public void guardarEstacion (int boton, float estacion);
      public double sintonizar (int posicion);
      public boolean getEstado();
      public boolean getfrecuencia();
      public double getEstacion();
    }


Clase:

    import java.util.Arrays;

    public class Radio implements InterfaceRadio {
    
    private boolean estado, amFm, frecuenia;
    private double estacion;
	
    public Radio(){
      estado = true;
      amFm = true;
      estacion = 57.9;
    }
    
     @Override
     public void cambiarEstado(boolean estado1) {
      estado = estado1;
      if(estado){
            estado = false;
    	}else{
            estado = true;
	    }	
    }
    
    @Override
    public void cambiarFrecuencia(boolean frecuencia1) {
       frecuencia = frecuencia1
        if(amFm){
            amFm = false;
	      }else{
            amFm = true;
      	}
    }
    
    @Override
    public void subirEstacion(double estacion1) {
        estacion = estacion1;
        if(amFm){
            if(estacion <= 107.9){
	            	estacion += 0.2;
            }else{
                estacion = 87.9;
            }
        }else{
            if(estacion <= 1610){
		            estacion += 10;
            }else{
	            	estacion = 530;
            }
        }
    }

    @Override
    public void bajarEstacion(double estacion1) {
       	estacion = estacion1
        if(amFm){
            if(estacion >= 87.9){
	            	estacion -= 0.2;
            }else{
		            estacion = 107.9;
            }
        }else{
            if(estacion >= 530){
		            estacion -= 10;
            }else{
	            	estacion = 1610;
            }
        }
    }

    @Override
    public void guardarEstacion(int boton, double estacion) {
        //implementar
    }

    @Override
    public double sintonizar() {
      //implementar    
    }

    
    public void setAmFm(boolean amFm) {
	    this.amFm = amFm;
	    if(amFm){
        estacion = 87.9;
	    }else{
        estacion = 530;
	    }
    }
    
    @Override
    public boolean getEstado() {
        return estado;
    }
    
    public void setEstado(boolean estado) {
    	this.estado = estado;
    }
    
    @Override
    public boolean getFrecuencia() {
        return amFm;
    }
    
    @Override
    public double getEstacion() {
        return estacion;
    }
   
    public void setEstacion(double estacion) {
	    this.estacion = estacion;
	  }
    }



Grafico:


	import javax.swing.JFrame;
	import javax.swing.JPanel;
	import javax.swing.border.EmptyBorder;
	import javax.swing.JButton;
	import javax.swing.JLabel;

	import java.awt.Font;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;

	public class GraficoRadio extends JFrame {
    	private JPanel contentPane;
    	private JButton btn1, btn2, btn3, btn4, btn5, btn6, btn7, btn8, btn9, btn10,btn11, btn12, btnEstado, 			btnanterior, btnsiguiente;
	private JLabel lblEmisora, lblEstacion;
	private InterfaceRadio miRadio;
    	private JLabel lblEmisora_1;
    	private JLabel lblFrecuencia;
    	private JButton btnCambiar;

    	public GraficoRadio(){
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	setBounds(100, 100, 450, 300);
	contentPane = new JPanel();
	contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
	setContentPane(contentPane);
	contentPane.setLayout(null);
   
        miRadio = new Radio();
        
        btn1 = new JButton("1");
	btn1.setBounds(51, 172, 46, 29);
	btn1.addActionListener(new ButtonListener());
	contentPane.add(btn1);
		
	btn2 = new JButton("2");
	btn2.setBounds(109, 172, 46, 29);
	btn2.addActionListener(new ButtonListener());
	contentPane.add(btn2);
		
	btn3 = new JButton("3");
	btn3.setBounds(167, 172, 46, 29);
	btn3.addActionListener(new ButtonListener());
	contentPane.add(btn3);
		
	btn4 = new JButton("4");
	btn4.setBounds(225, 172, 46, 29);
	btn4.addActionListener(new ButtonListener());
	contentPane.add(btn4);
		
	btn5 = new JButton("5");
	btn5.setBounds(283, 172, 46, 29);
	btn5.addActionListener(new ButtonListener());
	contentPane.add(btn5);
		
	btn6 = new JButton("6");
	btn6.setBounds(341, 172, 46, 29);
	btn6.addActionListener(new ButtonListener());
	contentPane.add(btn6);
		
	btn7 = new JButton("7");
	btn7.setBounds(51, 214, 46, 29);
	btn7.addActionListener(new ButtonListener());
	contentPane.add(btn7);
		
	btn8 = new JButton("8");
	btn8.setBounds(109, 214, 46, 29);
	btn8.addActionListener(new ButtonListener());
	contentPane.add(btn8);
		
	btn9 = new JButton("9");
	btn9.setBounds(167, 214, 46, 29);
	btn9.addActionListener(new ButtonListener());
	contentPane.add(btn9);
		
	btn10 = new JButton("10");
	btn10.setBounds(225, 213, 46, 29);
	btn10.addActionListener(new ButtonListener());
	contentPane.add(btn10);
		
	btn11 = new JButton("11");
	btn11.setBounds(283, 214, 46, 29);
	btn11.addActionListener(new ButtonListener());
	contentPane.add(btn11);
		
	btn12 = new JButton("12");
	btn12.setBounds(341, 214, 46, 29);
	btn12.addActionListener(new ButtonListener());
	contentPane.add(btn12);
		
	btnEstado = new JButton("Encendido");
	btnEstado.setBounds(167, 16, 107, 29);
	btnEstado.addActionListener(new ButtonListener());
	contentPane.add(btnEstado);
		
	lblEstacion = new JLabel(""+miRadio.getEstacion());
	lblEstacion.setFont(new Font("Lucida Grande", Font.PLAIN, 23));
	lblEstacion.setBounds(242, 57, 134, 29);
	contentPane.add(lblEstacion);
		
	lblEmisora = new JLabel("FM");
	lblEmisora.setFont(new Font("Lucida Grande", Font.PLAIN, 23));
	lblEmisora.setBounds(252, 93, 56, 29);
	contentPane.add(lblEmisora);
		
	btnanterior = new JButton("<<");
	btnanterior.setBounds(152, 131, 75, 29);
	btnanterior.addActionListener(new ButtonListener());
	contentPane.add(btnanterior);
		
	btnsiguiente = new JButton(">>");
	btnsiguiente.setBounds(242, 131, 75, 29);
	btnsiguiente.addActionListener(new ButtonListener());
	contentPane.add(btnsiguiente);
		
	lblEmisora_1 = new JLabel("Emisora");
	lblEmisora_1.setBounds(152, 67, 61, 16);
	contentPane.add(lblEmisora_1);
		
	lblFrecuencia = new JLabel("Frecuencia");
	lblFrecuencia.setBounds(152, 103, 75, 16);
	contentPane.add(lblFrecuencia);
		
	btnCambiar = new JButton("Cambiar ");
	btnCambiar.setBounds(51, 98, 93, 29);
	btnCambiar.addActionListener(new ButtonListener());
	contentPane.add(btnCambiar);
    
    }
   

