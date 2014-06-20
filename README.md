Base-de-Datos-20-06-14
======================

create procedure SP_CONSULTAFACTURASMES
@mes1 int, @mes2 int
as
begin
 select * from TB_FACTURA 
select * from TB_FACTURA where month(FEC_FAC)>=@mes1 and MONTH(FEC_FAC)<=@mes2
end

exec SP_CONSULTAFACTURASMES 1,3

create procedure SP_EJEM5
@letra1 char
as
begin
select * from TB_VENDEDOR where APE_VEN like @letra1+'%'
end

exec SP_EJEM5 a

create procedure SP_EJE
@parametro1 int, @parametro2 int
as
begin
select *from TB_PRODUCTO
where PRE_PRO between @parametro1 and @parametro2 
end

exec SP_EJE 1,305

// nuevo tema 



select NUM_FAC from TB_FACTURA

select RAZ_SOC_CLI, DIR_CLI from TB_CLIENTE


select * from TB_FACTURA F inner join TB_CLIENTE CI
ON F.COD_CLI=CI.COD_CLI

select F.NUM_FAC, F.FEC_FAC, CI.RAZ_SOC_CLI, CI.DIR_CLI
from TB_FACTURA F inner join TB_CLIENTE CI
ON F.COD_CLI=CI.COD_CLI
ORDER BY CI.RAZ_SOC_CLI,F.NUM_FAC

select V.COD_VEN, V.NOM_VEN, V.APE_VEN, D.NOM_DIS
from TB_VENDEDOR V inner join TB_DISTRITO D
ON V.COD_DIS=D.COD_DIS

select F.NUM_FAC, F.FEC_FAC, P.DES_PRO,A.COD_PRO,PR.RAZ_SOC_PRV
from TB_FACTURA F inner join TB_DETALLE_FACTURA DF 
ON F.NUM_FAC=DF.NUM_FAC
inner join TB_PRODUCTO P
ON DF.COD_PRO=P.COD_PRO
inner join TB_ABASTECIMIENTO A
ON DF.COD_PRO=A.COD_PRO and P.COD_PRO=A.COD_PRO
inner join TB_PROVEEDOR PR
ON A.COD_PRV=PR.COD_PRV
ORDER BY F.NUM_FAC


select PR.RAZ_SOC_PRV, P.DES_PRO
from TB_ABASTECIMIENTO A inner join TB_PROVEEDOR PR 
ON A.COD_PRV=PR.COD_PRV
inner join TB_PRODUCTO P
ON A.COD_PRO=P.COD_PRO
ORDER BY RAZ_SOC_PRV 
