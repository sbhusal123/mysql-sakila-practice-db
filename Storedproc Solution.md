**1. Create a basic stored procedure to display the first_name of the actor, provided actor_id.**

```sql
-- delimeter specifies the begining and end of the code/data

delimiter // 
-- use delimeter //

create procedure spGetActor(sp_actor_id int)
begin
	select 
		first_name
    from 
		actor
    where
		actor_id=sp_actor_id;
end //

delimiter ; 
-- restore default delimeter colon(;)

-- can be called using:
call sakila.spGetActor(10)

```