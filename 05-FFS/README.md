# Lab 5: Samuel Gubi

## Pre-Lab preparation

1. Write characteristic equations and complete truth tables for D, JK, T flip-flops where `q(n)` represents main output value before the clock edge and `q(n+1)` represents output value after the clock edge.   

![Characteristic equations](./rovnice_de1.png)

   **D-type FF**
   | **clk** | **d** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 0 | 0 | `q(n+1)` has the same level as `d` |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 1 | 0 | `q(n+1)` has the same level as `d` |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 0 | 1 | `q(n+1)` has the same level as `d` |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 1 | 1 | `q(n+1)` has the same level as `d` |

   **JK-type FF**
   | **clk** | **j** | **k** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-: | :-- |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 0 | 0 | 1 | Output did not change |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 0 | 1 | 0 | Output did not change |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 1 | 0 | 0 | Reset |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 1 | 0 | 0 | Reset |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 0 | 1 | 1 | Set |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 0 | 1 | 1 | Set |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 1 | 1 | 1 | Toogle |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 1 | 0 | 0 | Toogle |

   **T-type FF**
   | **clk** | **t** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ![rising](./%C5%A1ipka_de1.png)) | 0 | 0 | 0 | Output did not change |
   | ![rising](./%C5%A1ipka_de1.png) | 0 | 1 | 1 | Output did not change |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 0 | 1 | Toogle |
   | ![rising](./%C5%A1ipka_de1.png) | 1 | 1 | 0 | Toogle |

<a name="part1"></a>

### D & T Flip-flops

1. Screenshot with simulated time waveforms. Try to simulate both D- and T-type flip-flops in a single testbench with a maximum duration of 200 ns, including reset. Always display all inputs and outputs (display the inputs at the top of the image, the outputs below them) at the appropriate time scale!

   ![your figure](screen_Gub.PNG)

### JK Flip-flop

1. Listing of VHDL architecture for JK-type flip-flop. Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

```vhdl
architecture Behavioral of jk_ff_rst is

    signal sig_q : std_logic;
begin
    p_jk_ff_rst : process (clk)
    begin
        if rising_edge(clk) then
        -- WRITE YOUR CODE HERE

            if (j = '0' and k = '1') then 
                sig_q     <= '0';
                
            elsif (j = '0' and k = '0') then
                sig_q     <= sig_q;
                
            elsif (j = '1' and k = '0') then
                sig_q     <= '1';
             
            elsif (j = '1' and k = '1') then 
                sig_q <= not sig_q;
                
            elsif (rst = '1') then 
            	sig_q <= '0';

            end if;
        end if;
    end process p_jk_ff_rst;

    -- Output ports are permanently connected to local signal
    q     <= sig_q;
    q_bar <= not sig_q;
end architecture Behavioral;

```
### Screen of working JK

![your figure](Screen_jk.png)
( V textových súboroch mám len programy s ktorými som pracoval v EDU. a toto je výsledok )

### Shift register

1. Image of `top` level schematic of the 4-bit shift register. Use four D-type flip-flops and connect them properly. The image can be drawn on a computer or by hand. Always name all inputs, outputs, components and internal signals!

   ![your figure](Shift_register.jpeg)

