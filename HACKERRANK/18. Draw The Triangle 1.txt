set @number = 21;
select repeat('* ', @number := @number - 1) from information_schema.tables;