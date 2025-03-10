```
library IEEE;
use IEEE.std_logic_1164.all;

entity or2 is
    port ( y : out std_logic;
           x1, x2 : in std_logic);
end entity or2;

architecture behavior of or2 is
begin
    y <= x1 or x2;
end architecture behavior;
```