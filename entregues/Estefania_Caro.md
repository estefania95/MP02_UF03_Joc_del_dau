# Versió definitiva
La meva funció retorna  un boleà, si no es queda amb els punts retorna un 0, i si es queda els punts retorna un 1.

```

create function mElsQuedo (@num_jugador as int, @punts as int)
returns int
as begin
	create function mElsQuedo (@num_jugador as int, @punts as int)
returns int
as begin
	declare @donar as bit
	declare @puntsTotals1 as int, @puntsTotals2 as int
	set @puntsTotals1 = (select sum(puntsAnotats) from Marcadors where @num_jugador = nJugadorAnota)
	set @puntsTotals2 = (select sum(puntsAnotats) from Marcadors where @num_jugador != nJugadorAnota)
	
	if (@puntsTotals1<@puntsTotals2)
	begin
		set @donar = 1;
	end
	else
	begin
		if(@punts <3)
		begin
			set @donar = 0;
		end
		else
		begin
			set @donar = 1;
		end
	end
	return @donar
end
end

```
