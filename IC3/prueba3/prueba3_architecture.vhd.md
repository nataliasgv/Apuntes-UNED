```
library IEEE;
use IEEE.std_logic_1164.all;

architecture estructura of prueba3_entity is

component or2 is
	port ( y : out std_logic;
		x1, x2 : in std_logic);
end component or2;

component not1 is
	port ( y : out std_logic;
		x : in std_logic);
end component not1;

signal xory, xoryorz: std_logic;

begin
	or2_1 : or2 port map ( y => xory, x1 => x, x2 => y);
	or2_2 : or2 port map ( y => xoryorz, x1 => xory, x2 => z);
	Inv_1 : not1 port map ( y => f, x => xoryorz);
end architecture estructura;
```