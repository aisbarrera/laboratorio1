laboratorio1
============

radio


Interfaz:


    public interface InterfaceRadio {
      public void cambiarEstado(Boolean estado);
      public void cambiarFrecuencia(Boolean estado); /// am false fm true
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
    
    private boolean estado, amFm;
    private double estacion;
	
    public Radio(){
      estado = true;
      amFm = true;
      estacion = 57.9;
    }
    
     @Override
     public void cambiarEstado() {
      if(estado){
            estado = false;
    	}else{
            estado = true;
	    }	
    }
    
    @Override
    public void cambiarFrecuencia() {
        if(amFm){
            amFm = false;
	      }else{
            amFm = true;
      	}
    }
    
    @Override
    public void subirEstacion() {
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
    public void bajarEstacion() {
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

