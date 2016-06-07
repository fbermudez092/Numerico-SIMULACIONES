# Numerico-SIMULACIONES

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%                                                   %%%%%%%%%%%%%%
%%%%%%%%%%%%%                     SIMULACIONES                  %%%%%%%%%%%%%%
%%%%%%%%%%%%%                                                   %%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%                                                                    %%%%%
%%%%%                      DEFINICIÓN DEL PROBLEMA:                      %%%%%
%%%%%    Completar la estimación de la probabilidad de que un neutrón    %%%%%     
%%%%%     pueda salir de una pared de plomo de 5 unidades de espesor     %%%%%
%%%%%                                                                    %%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%                                                                 %%%%%
%%%%%                      VALORES DE ENTRADA:                        %%%%%
%%%%% n: Número de neutrones que se utilizan para el blindaje         %%%%%     
%%%%% t: Número de veces que se repite el proceso de blindaje para    %%%%%
%%%%%    los n neutrones                                              %%%%%   
%%%%%                                                                 %%%%%
%%%%%                      VALORES DE SALIDA:                         %%%%%
%%%%%          la función devuelve un vector [Probabilidad]           %%%%%     
%%%%% [Probabilidad]: Es la probabilidad de que salga un Neutron de   %%%%%
%%%%%                 una pared de plomo de 5 unidades de espesor     %%%%%   
%%%%%                                                                 %%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

function [Probabilidad] = Simulation(n,t)
  if n<=0 || t<=0;       %Verifica que el número de neutrones y repetición es mayor a cero 
    error ('Ingrese un numero de neutrones y  repetición mayores a cero');
  else
    m=0;
    p=0;
    R=2*pi*rand(n,7);   %Genera una matríz con los angulos de movimiento para cada neutron
    for k=1:t
    	for i=1:n;
      	x=1;
       	for j=1:7;
        	x=x+cos(R(i,j));
         	if x<0;        %Verifica que no se ha salido
          	break
         	elseif x>5;    %Verifica que no se ha salido
           	m=m+1;
           	break
         	end
       	end
     	end
  	end
		Probabilidad=m/(t*n);  %Calcula la Probabilidad
end
