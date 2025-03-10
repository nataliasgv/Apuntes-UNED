```
library IEEE;
use IEEE.std_logic_1164.all;

entity prueba3_TB is
end entity prueba3_TB;


architecture test of prueba3_TB is

	signal x,y,z,f: std_logic := '0';

begin

	UUT: entity work.prueba3_entity port map (f => f, x=> x, y => y, z => z);

	process
	begin
	 -- Prueba 1: 000 -> f = 1
	x <= '0'; y <= '0'; z <= '0'; wait for 10 ns;

	 -- Prueba 2: 001 -> f = 0
        x <= '0'; y <= '0'; z <= '1'; wait for 10 ns;
        
        -- Prueba 3: 010 -> f = 0
        x <= '0'; y <= '1'; z <= '0'; wait for 10 ns;
        
        -- Prueba 4: 011 -> f = 0
        x <= '0'; y <= '1'; z <= '1'; wait for 10 ns;
```