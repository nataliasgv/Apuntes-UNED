```
library IEEE;
use IEEE.std_logic_1164.all;

entity not1 is
    port ( y : out std_logic;
           x : in std_logic);
end entity not1;

architecture behavior of not1 is
begin
    y <= not x;
end architecture behavior;

```