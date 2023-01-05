


module N_bit_shift(reset,clk,load,dir,out,R,w);
  parameter n = 4;
  input reset,dir,load,clk,w;
  input [n-1:0]R;
   output reg [n-1:0]out;
  integer k;
  always @(posedge clk,negedge reset)
    begin
      if(!reset)
        out <= 0;
      else if(load)
        out <= R;
      else 
        begin
          if(dir)
            begin
              
              for(k=0;k<n;k=k+1)
                out[k+1] <= out[k];
              out[0] <= w;
              end
          else if(!dir)
            begin
              for(k=0;k<n;k=k+1)
                out[k] <= out[k+1];
              out[n-1] <= w;
            end
        end
    end
 
  
  
endmodule






