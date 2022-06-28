# OpenEye-Command-lines

Below are the commands shown used to initiate the docking of 40 inhibitors to gal-7.



**Flipper - Tautomers**

Flipper:

*flipper -warts -in HitsAndActives.smi -out Flipper/HitsAndActives_Flip.oeb*

Tautomers:

*tautomers -warts -in Flipper/HitsAndActives_Flip.oeb -maxgenerated 1 -out Tautomers/HitsAndActives_Flip_Tau.oeb*

Oeomega:

*oeomega classic -in Tautomers/HitsAndActives_Flip_Tau.oeb -prefix actives_omega -progress percent -status actives_stat.report -maxconfs 200 -out Omega/HitsAndActives_Flip_Tau_Omega.oeb*

HYBRID:

*hybrid -mpi_np 4 -receptor 5h9q_1Constraints.oedu -dbase Omega/HitsAndActives_Flip_Tau_Omega.oeb -dock_resolution High -docked_molecule_file HYBRID_Docked.oeb -undocked_molecule_file HYBRID_Undocked.oeb -score_file HYBRID_Docking_Score.txt -report_file HYBRID_Docking_Report.txt -settings_file HYBRID_Docking_Settings.txt -status_file HYBRID_Docking_Status.txt -hitlist_size 1000 -num_poses 1*

FRED:

*fred -mpi_np 4 -receptor 5h9q_1NOconstraints.oedu -dbase Omega/HitsAndActives_Flip_Tau_Omega.oeb -dock_resolution High -docked_molecule_file Fred_Docked.oeb -undocked_molecule_file Fred_Undocked.oeb -score_file Fred_Docking_Score.txt -report_file Fred_Docking_Report.txt -settings_file Fred_Docking_Settings.txt -status_file Fred_Docking_Status.txt -hitlist_size 1000 -num_poses 1*


**Tautomers - Flipper**

Tautomers:

*tautomers -warts -in HitsAndActives.smi -maxgenerated 1 -out Tautomers/HitsAndActives_Tau.oeb*

Flipper:

*flipper -warts -in Tautomers/HitsAndActives_Tau.oeb -out Flipper/HitsAndActives_Tau_Flip.oeb*

Oeomega: 

*oeomega classic -in Flipper/HitsAndActives_Tau_Flip.oeb -prefix actives_omega -progress percent -status actives_stat.report -maxconfs 200 -out Omega/HitsAndActives_Tau_Flip_Omega.oeb*

HYBRID:

*hybrid -receptor 5h9q_1Constraints.oedu -dbase Omega/HitsAndActives_Tau_Flip_Omega.oeb -dock_resolution High -docked_molecule_file HYBRID_Active.oeb -undocked_molecule_file HYBRID_Undocked_Active.oeb -score_file HYBRID_Active_score.txt -report_file HYBRID_Active_score.txt -settings_file HYBRID_Active_settings.txt -status_file HYBRID_Active_status.txt -hitlist_size 1000 -num_poses 1*

FRED:

*fred -receptor 5h9q_1NOconstraints.oedu -dbase Omega/HitsAndActives_Tau_Flip_Omega.oeb -dock_resolution High -docked_molecule_file Fred_Active.oeb -undocked_molecule_file Fred_Undocked_Active.oeb -score_file Fred_Active_score.txt -report_file Fred_Active_score.txt -settings_file Fred_Active_settings.txt -status_file Fred_Active_status.txt -hitlist_size 1000 -num_poses 1*
