# PlSql
Procedures
create or replace procedure lab_atualizar_result_pardini(	ds_campo_valor_p			varchar2,
										valor_exame_filho_P			varchar2,
										ds_unidade_medida_p			varchar2,
										ds_referencia_p 			varchar2,
										ds_observacao_p		  		varchar2,
										nr_seq_resultado_p			varchar2,
										nr_seq_exame_p				varchar2,
										nr_seq_prescr_p				varchar2,
										sql_unid_med_p				varchar2,
										sql_unid_med_bv				varchar2,
										sql_refer_p					varchar2,
										sql_refer_bv				varchar2,
										sql_observacao_p			varchar2,
										sql_observacao_bv			varchar2,
										nm_usuario_p				Varchar2) is

begin

if  (nr_seq_resultado_p is not null) and
	(nr_seq_prescr_p	is not null) and
	(nr_seq_exame_p 	is not null) then

	if (upper(ds_campo_valor_p) = upper('ds_resultado')) then
		update 	exame_lab_result_item
		set 	ds_resultado	 	= valor_exame_filho_p,
				qt_resultado		= null,
				pr_resultado		= null,
				nm_usuario 		 	= nm_usuario_p,
				ds_unidade_medida 	= ds_unidade_medida_p,
				ds_referencia 		= ds_referencia_p,
				ds_referencia_ext 	= ds_referencia_p,
				ds_observacao		= ds_observacao_p
		where 	nr_seq_resultado 	= nr_seq_resultado_p
		and 	nr_seq_exame 		= nr_seq_exame_p
		and 	nr_seq_prescr 		= nr_seq_prescr_p;
	elsif(upper(ds_campo_valor_p) = upper('qt_resultado')) then
		update 	exame_lab_result_item
		set 	ds_resultado	 	= '',
				qt_resultado		= valor_exame_filho_p,
				pr_resultado		= null,
				nm_usuario 		 	= nm_usuario_p,
				ds_unidade_medida 	= ds_unidade_medida_p,
				ds_referencia 		= ds_referencia_p,
				ds_referencia_ext 	= ds_referencia_p,
				ds_observacao		= ds_observacao_p
		where 	nr_seq_resultado 	= nr_seq_resultado_p
		and 	nr_seq_exame 		= nr_seq_exame_p
		and 	nr_seq_prescr 		= nr_seq_prescr_p;
	else
		update 	exame_lab_result_item
		set 	ds_resultado	 	= '',
				qt_resultado		= null,
				pr_resultado		= valor_exame_filho_p,
				nm_usuario 		 	= nm_usuario_p,
				ds_unidade_medida 	= ds_unidade_medida_p,
				ds_referencia 		= ds_referencia_p,
				ds_referencia_ext 	= ds_referencia_p,
				ds_observacao		= ds_observacao_p
		where 	nr_seq_resultado 	= nr_seq_resultado_p
		and 	nr_seq_exame 		= nr_seq_exame_p
		and 	nr_seq_prescr 		= nr_seq_prescr_p;

	end if;

end if;

commit;

end lab_atualizar_result_pardini;

