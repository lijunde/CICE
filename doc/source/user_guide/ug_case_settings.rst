:tocdepth: 3

.. _case_settings:

Case Settings
=====================

There are two important files that define the case, **cice.settings** and 
**ice_in**.  **cice.settings** is a list of env variables that define many
values used to setup, build and run the case.  **ice_in** is the input namelist file
for CICE.  Variables in both files are described below.

.. _tabsettings:

Table of CICE Settings
--------------------------

The **cice.settings** file is reasonably well self documented.  Several of
the variables defined in the file are not used in CICE.  They exist
to support the CICE model.

.. csv-table:: *CICE settings*
   :header: "variable", "options/format", "description", "recommended value"
   :widths: 15, 15, 25, 20

   "ICE_CASENAME", " ", "case name", "set by cice.setup"
   "ICE_SANDBOX", " ", "sandbox directory", "set by cice.setup"
   "ICE_MACHINE", " ", "machine name", "set by cice.setup"
   "ICE_COMPILER", " ", "environment name", "set by cice.setup"
   "ICE_MACHCOMP", " ", "machine_environment name", "set by cice.setup"
   "ICE_SCRIPTS", " ", "scripts directory", "set by cice.setup"
   "ICE_CASEDIR", " ", "case directory", "set by cice.setup"
   "ICE_RUNDIR", " ", "run directory", "set by cice.setup"
   "ICE_OBJDIR", " ", "compile directory", "${ICE_RUNDIR}/compile"
   "ICE_RSTDIR", " ", "unused", "${ICE_RUNDIR}/restart"
   "ICE_HSTDIR", " ", "unused", "${ICE_RUNDIR}/history"
   "ICE_LOGDIR", " ", "log directory", "${ICE_CASEDIR}/logs"
   "ICE_DRVOPT", " ", "unused", "cice"
   "ICE_IOTYPE", " ", "unused", "netcdf"
   "ICE_CLEANBUILD", "true,false", "automatically clean before building", "true"
   "ICE_GRID", "col", "grid", "set by cice.setup"
   "ICE_NXGLOB", "integer", "number of gridcells", "set by cice.setup"
   "ICE_NTASKS", "integer", "number of tasks, must be set to 1", "set by cice.setup"
   "ICE_NTHRDS", "integer", "number of threads per task, must be set to 1", "set by cice.setup"
   "ICE_BLCKX", "integer", "block size in x direction", "set by cice.setup"
   "ICE_BLCKY", "integer", "block size in y direction", "set by cice.setup"
   "ICE_MXBLCKS", "integer", "maximum number of blocks per task", "set by cice.setup"
   "ICE_TEST", " ", "test setting if using a test", "set by cice.setup"
   "ICE_TESTNAME", " ", "test name if using a test", "set by cice.setup"
   "ICE_BASELINE", " ", "baseline directory name, associated with cice.setup -bdir ", "set by cice.setup"
   "ICE_BASEGEN", " ", "baseline directory name for regression generation, associated with cice.setup -bgen ", "set by cice.setup"
   "ICE_BASECOM", " ", "baseline directory name for regression comparison, associated with cice.setup -bcmp ", "set by cice.setup"
   "ICE_BFBCOMP", " ", "location of case for comparison, associated with cice.setup -td", "set by cice.setup"
   "ICE_SPVAL", " ", "special value for cice.settings strings", "set by cice.setup"
   "ICE_RUNLENGTH", " ", "batch run length default", "set by cice.setup"
   "ICE_ACCOUNT", " ", "batch account number", "set by cice.setup or by default"
   "ICE_THREADED", "true,false", "force threading in compile, will always compile threaded if NTHRDS is gt 1", "false"
   "NICELYR", "integer", "number of vertical layers in the ice", "7"
   "NSNWLYR", "integer", "number of vertical layers in the snow", "1"
   "NICECAT", "integer", "number of ice thickness categories", "5"
   "TRAGE", "0,1", "ice age tracer", "1"
   "TRFY", "0,1", "first-year ice area tracer", "1"
   "TRLVL", "0,1", "deformed ice tracer", "1"
   "TRPND", "0,1", "melt pond tracer", "1"
   "NTRAERO", "integer", "number of aerosol tracers", "1"
   "TRBRI", "0,1", "brine height tracer", "0"
   "TRZS", "0,1", "zsalinity tracer, needs TRBRI=1", "0"
   "TRBGCS", "0,1", "skeletal layer tracer, needs TRBGCZ=0", "0"
   "TRBGCZ", "0,1", "zbgc tracers, needs TRBGCS=0 and TRBRI=1", "0"
   "NBGCLYR", "integer", "number of zbgc layers", "7"
   "TRZAERO", "0-6", "number of z aerosol tracers", "0"
   "TRALG", "0,1,2,3", "number of algal tracers", "0"
   "TRDOC", "0,1,2,3", "number of dissolved organic carbon", "0"
   "TRDIC", "0,1", "number of dissolved inorganic carbon", "0"
   "TRDON", "0,1", "number of dissolved organic nitrogen", "0"
   "TRFEP", "0,1,2", "number of particulate iron tracers", "0"
   "TRFED", "0,1,2", "number of dissolved iron tracers", "0"
   "CAM_ICE", " ", "unused", "no"
   "DITTO", "no,yes", "turn on bit-for-bit global sums via real16", "no"
   "BARRIERS", "no,yes", "turn on barriers between global scatters and gathers", "no"
   "ICE_BLDDEBUG", "true,false", "turn on compile debug flags", "false"
   "NUMIN", "integer", "smallest unit number assigned to CICE files", "11"
   "NUMAX", "integer", "largest unit number assigned to CICE files", "99"



.. _tabnamelist:


Table of namelist options
-------------------------------

.. csv-table:: *Namelist options*
   :header: "variable", "options/format", "description", "recommended value"
   :widths: 15, 15, 30, 15 

   "*setup_nml*", "", "", ""
   "", "", "*Time, Diagnostics*", ""
   "``days_per_year``", "``360`` or ``365``", "number of days in a model year", "365"
   "``use_leap_years``", "true/false", "if true, include leap days", ""
   "``year_init``", "yyyy", "the initial year, if not using restart", ""
   "``istep0``", "integer", "initial time step number", "0"
   "``dt``", "seconds", "thermodynamics time step length", "3600."
   "``npt``", "integer", "total number of time steps to take", ""
   "``ndtd``", "integer", "number of dynamics/advection/ridging/steps per thermo timestep", "1"
   "", "", "*Initialization/Restarting*", ""
   "``runtype``", "``initial``", "start from ``ice_ic``", ""
   "", "``continue``", "restart using ``pointer_file``", ""
   "``ice_ic``", "``default``", "latitude and sst dependent", "default"
   "", "``none``", "no ice", ""
   "", "path/file", "restart file name", ""
   "``restart``", "true/false", "initialize using restart file", "``.true.``"
   "``use_restart_time``", "true/false", "set initial date using restart file", "``.true.``"
   "``restart_format``", "nc", "read/write  restart files (use with PIO)", ""
   "", "bin", "read/write binary restart files", ""
   "``lcdf64``", "true/false", "if true, use 64-bit  format", ""
   "``restart_dir``", "path/", "path to restart directory", ""
   "``restart_ext``", "true/false", "read/write halo cells in restart files", ""
   "``restart_file``", "filename prefix", "output file for restart dump", "‘iced’"
   "``pointer_file``", "pointer filename", "contains restart filename", ""
   "``dumpfreq``", "``y``", "write restart every ``dumpfreq_n`` years", "y"
   "", "``m``", "write restart every ``dumpfreq_n`` months", ""
   "", "``d``", "write restart every ``dumpfreq_n`` days", ""
   "``dumpfreq_n``", "integer", "frequency restart data is written", "1"
   "``dump_last``", "true/false", "if true, write restart on last time step of simulation", ""
   "", "", "*Model Output*", ""
   "``bfbflag``", "true/false", "for bit-for-bit diagnostic output", ""
   "``diagfreq``", "integer", "frequency of diagnostic output in ``dt``", "24"
   "", "*e.g.*, 10", "once every 10 time steps", ""
   "``diag_type``", "``stdout``", "write diagnostic output to stdout", ""
   "", "``file``", "write diagnostic output to file", ""
   "``diag_file``", "filename", "diagnostic output file (script may reset)", ""
   "``print_global``", "true/false", "print diagnostic data, global sums", "``.false.``"
   "``print_points``", "true/false", "print diagnostic data for two grid points", "``.false.``"
   "``latpnt``", "real", "latitude of (2) diagnostic points", "" 
   "``lonpnt``", "real", "longitude of (2) diagnostic points", ""
   "``dbug``", "true/false", "if true, write extra diagnostics", "``.false.``"
   "``histfreq``", "string array", "defines output frequencies", ""
   "", "``y``", "write history every ``histfreq_n`` years", ""
   "", "``m``", "write history every ``histfreq_n`` months", ""
   "", "``d``", "write history every ``histfreq_n`` days", ""
   "", "``h``", "write history every ``histfreq_n`` hours", ""
   "", "``1``", "write history every time step", ""
   "", "``x``", "unused frequency stream (not written)", ""
   "``histfreq_n``", "integer array", "frequency history output is written", ""
   "", "0", "do not write to history", ""
   "``hist_avg``", "true", "write time-averaged data", "``.true.``"
   "", "false", "write snapshots of data", ""
   "``history_dir``", "path/", "path to history output directory", ""
   "``history_file``", "filename prefix", "output file for history", "‘iceh’"
   "``write_ic``", "true/false", "write initial condition", ""
   "``incond_dir``", "path/", "path to initial condition directory", ""
   "``incond_file``", "filename prefix", "output file for initial condition", "‘iceh’"
   "``runid``", "string", "label for run (currently CESM only)", ""
   "", "", "", ""
   "*grid_nml*", "", "", ""
   "", "", "*Grid*", ""
   "``grid_format``", "``nc``", "read  grid and kmt files", "‘bin’"
   "", "``bin``", "read direct access, binary file", ""
   "``grid_type``", "``rectangular``", "defined in *rectgrid*", ""
   "", "``displaced_pole``", "read from file in *popgrid*", ""
   "", "``tripole``", "read from file in *popgrid*", ""
   "", "``regional``", "read from file in *popgrid*", ""
   "``grid_file``", "filename", "name of grid file to be read", "‘grid’"
   "``kmt_file``", "filename", "name of land mask file to be read", "‘kmt’"
   "``gridcpl_file``", "filename", "input file for coupling grid info", ""
   "``kcatbound``", "``0``", "original category boundary formula", "0"
   "", "``1``", "new formula with round numbers", ""
   "", "``2``", "WMO standard categories", ""
   "", "``-1``", "one category", ""
   "", "", "", ""
   "*domain_nml*", "", "", ""
   "", "", "*Domain*", ""
   "``nprocs``", "integer", "number of processors to use", ""
   "``processor_shape``", "``slenderX1``", "1 processor in the y direction (tall, thin)", ""
   "", "``slenderX2``", "2 processors in the y direction (thin)", ""
   "", "``square-ice``", "more processors in x than y, :math:`\sim` square", ""
   "", "``square-pop``", "more processors in y than x, :math:`\sim` square", ""
   "``distribution_type``", "``cartesian``", "distribute blocks in 2D Cartesian array", ""
   "", "``roundrobin``", "1 block per proc until blocks are used", ""
   "", "``sectcart``", "blocks distributed to domain quadrants", ""
   "", "``sectrobin``", "several blocks per proc until used", ""
   "", "``rake``", "redistribute blocks among neighbors", ""
   "", "``spacecurve``", "distribute blocks via space-filling curves", ""
   "", "``spiralcenter``", "distribute blocks via roundrobin from center of grid outward in a spiral", ""
   "", "``wghtfile``", "distribute blocks based on weights specified in ``distribution_wght_file``", ""
   "``distribution_wght``", "``block``", "full block size sets ``work_per_block``", ""
   "", "``latitude``", "latitude/ocean sets ``work_per_block``", ""
   "``distribution_wght_file``", "filename", "distribution weight file when distribution_type is ``wghtfile``", ""
   "``ew_boundary_type``", "``cyclic``", "periodic boundary conditions in x-direction", ""
   "", "``open``", "Dirichlet boundary conditions in x", ""
   "``ns_boundary_type``", "``cyclic``", "periodic boundary conditions in y-direction", ""
   "", "``open``", "Dirichlet boundary conditions in y", ""
   "", "``tripole``", "U-fold tripole boundary conditions in y", ""
   "", "``tripoleT``", "T-fold tripole boundary conditions in y", ""
   "``maskhalo_dyn``", "true/false", "mask unused halo cells for dynamics", ""
   "``maskhalo_remap``", "true/false", "mask unused halo cells for transport", ""
   "``maskhalo_bound``", "true/false", "mask unused halo cells for boundary updates", ""
   "", "", "", ""
   "*tracer_nml*", "", "", ""
   "", "", "*Tracers*", ""
   "``tr_iage``", "true/false", "ice age", ""
   "``restart_age``", "true/false", "restart tracer values from file", ""
   "``tr_FY``", "true/false", "first-year ice area", ""
   "``restart_FY``", "true/false", "restart tracer values from file", ""
   "``tr_lvl``", "true/false", "level ice area and volume", ""
   "``restart_lvl``", "true/false", "restart tracer values from file", ""
   "``tr_pond_cesm``", "true/false", "CESM melt ponds", ""
   "``restart_pond_cesm``", "true/false", "restart tracer values from file", ""
   "``tr_pond_topo``", "true/false", "topo melt ponds", ""
   "``restart_pond_topo``", "true/false", "restart tracer values from file", ""
   "``tr_pond_lvl``", "true/false", "level-ice melt ponds", ""
   "``restart_pond_lvl``", "true/false", "restart tracer values from file", ""
   "``tr_aero``", "true/false", "aerosols", ""
   "``restart_aero``", "true/false", "restart tracer values from file", ""
   "*thermo_nml*", "", "", ""
   "", "", "*Thermodynamics*", ""
   "``kitd``", "``0``", "delta function ITD approximation", "1"
   "", "``1``", "linear remapping ITD approximation", ""
   "``ktherm``", "``0``", "zero-layer thermodynamic model", ""
   "", "``1``", "Bitz and Lipscomb thermodynamic model", ""
   "", "``2``", "mushy-layer thermodynamic model", ""
   "``conduct``", "``MU71``", "conductivity :cite:`MU71`", ""
   "", "``bubbly``", "conductivity :cite:`PETB07`", ""
   "``a_rapid_mode``", "real", "brine channel diameter", "0.5x10 :math:`^{-3}` m"
   "``Rac_rapid_mode``", "real", "critical Rayleigh number", "10"
   "``aspect_rapid_mode``", "real", "brine convection aspect ratio", "1"
   "``dSdt_slow_mode``", "real", "drainage strength parameter", "-1.5x10 :math:`^{-7}` m/s/K"
   "``phi_c_slow_mode``", ":math:`0<\phi_c < 1`", "critical liquid fraction", "0.05"
   "``phi_i_mushy``", ":math:`0<\phi_i < 1`", "solid fraction at lower boundary", "0.85"
   "", "", "", ""
   "*dynamics_nml*", "", "", ""
   "", "", "*Dynamics*", ""
   "``kdyn``", "``0``", "dynamics OFF", "1"
   "", "``1``", "EVP dynamics", ""
   "", "``2``", "EAP dynamics", ""
   "``revised_evp``", "true/false", "use revised EVP formulation", ""
   "``ndte``", "integer", "number of EVP subcycles", "120"
   "``advection``", "``remap``", "linear remapping advection", "‘remap’"
   "", "``upwind``", "donor cell advection", ""
   "``kstrength``", "``0``", "ice strength formulation :cite:`Hibler79`", "1"
   "", "``1``", "ice strength formulation :cite:`Rothrock75`", ""
   "``krdg_partic``", "``0``", "old ridging participation function", "1"
   "", "``1``", "new ridging participation function", ""
   "``krdg_redist``", "``0``", "old ridging redistribution function", "1"
   "", "``1``", "new ridging redistribution function", ""
   "``mu_rdg``", "real", "e-folding scale of ridged ice", ""
   "``Cf``", "real", "ratio of ridging work to PE change in ridging", "17."
   "", "", "", ""
   "*shortwave_nml*", "", "", ""
   "", "", "*Shortwave*", ""
   "``shortwave``", "``default``", "NCAR CCSM3 distribution method", ""
   "", "``dEdd``", "Delta-Eddington method", ""
   "``albedo_type``", "``default``", "NCAR CCSM3 albedos", "‘default’"
   "", "``constant``", "four constant albedos", ""
   "``albicev``", ":math:`0<\alpha <1`", "visible ice albedo for thicker ice", ""
   "``albicei``", ":math:`0<\alpha <1`", "near infrared ice albedo for thicker ice", ""
   "``albsnowv``", ":math:`0<\alpha <1`", "visible, cold snow albedo", ""
   "``albsnowi``", ":math:`0<\alpha <1`", "near infrared, cold snow albedo", ""
   "``ahmax``", "real", "albedo is constant above this thickness", "0.3 m"
   "``R_ice``", "real", "tuning parameter for sea ice albedo from Delta-Eddington shortwave", ""
   "``R_pnd``", "real", "... for ponded sea ice albedo …", ""
   "``R_snw``", "real", "... for snow (broadband albedo) …", ""
   "``dT_mlt``", "real", ":math:`\Delta` temperature per :math:`\Delta` snow grain radius", ""
   "``rsnw_mlt``", "real", "maximum melting snow grain radius", ""
   "``kalg``", "real", "absorption coefficient for algae", ""
   "", "", "", ""
   "*ponds_nml*", "", "", ""
   "", "", "*Melt Ponds*", ""
   "``hp1``", "real", "critical ice lid thickness for topo ponds", "0.01 m"
   "``hs0``", "real", "snow depth of transition to bare sea ice", "0.03 m"
   "``hs1``", "real", "snow depth of transition to pond ice", "0.03 m"
   "``dpscale``", "real", "time scale for flushing in permeable ice", ":math:`1\times 10^{-3}`"
   "``frzpnd``", "``hlid``", "Stefan refreezing with pond ice thickness", "‘hlid’"
   "", "``cesm``", "CESM refreezing empirical formula", ""
   "``rfracmin``", ":math:`0 \le r_{min} \le 1`", "minimum melt water added to ponds", "0.15"
   "``rfracmax``", ":math:`0 \le r_{max} \le 1`", "maximum melt water added to ponds", "1.0"
   "``pndaspect``", "real", "aspect ratio of pond changes (depth:area)", "0.8"
   "", "", "", ""
   "*zbgc_nml*", "", "", ""
   "", "", "*Biogeochemistry*", ""
   "``tr_brine``", "true/false", "brine height tracer", ""
   "``tr_zaero``", "true/false", "vertical aerosol tracers", ""
   "``modal_aero``", "true/false", "modal aersols", ""
   "``restore_bgc``", "true/false", "restore bgc to data", ""
   "``solve_zsal`", "true/false", "update salinity tracer profile", ""
   "``bgc_data_dir``", "path/", "data directory for bgc", ""
   "``skl_bgc``", "true/false", "biogeochemistry", ""
   "``sil_data_type``", "``default``", "default forcing value for silicate", ""
   "", "``clim``", "silicate forcing from ocean climatology :cite:`GLBA06`", ""
   "``nit_data_type``", "``default``", "default forcing value for nitrate", ""
   "", "``clim``", "nitrate forcing from ocean climatology :cite:`GLBA06`", ""
   "", "``sss``", "nitrate forcing equals salinity", ""
   "``fe_data_type``", "``default``", "default forcing value for iron", ""
   "", "``clim``", "iron forcing from ocean climatology", ""
   "``bgc_flux_type``", "``Jin2006``", "ice–ocean flux velocity of :cite:`JDWSTWLG06`", ""
   "", "``constant``", "constant ice–ocean flux velocity", ""
   "``restart_bgc``", "true/false", "restart tracer values from file", ""
   "``tr_bgc_C_sk``", "true/false", "algal carbon tracer", ""
   "``tr_bgc_chl_sk``", "true/false", "algal chlorophyll tracer", ""
   "``tr_bgc_Am_sk``", "true/false", "ammonium tracer", ""
   "``tr_bgc_Sil_sk``", "true/false", "silicate tracer", ""
   "``tr_bgc_DMSPp_sk``", "true/false", "particulate DMSP tracer", ""
   "``tr_bgc_DMSPd_sk``", "true/false", "dissolved DMSP tracer", ""
   "``tr_bgc_DMS_sk``", "true/false", "DMS tracer", ""
   "``phi_snow``", "real", "snow porosity for brine height tracer", ""
   "", "", "", ""
   "*forcing_nml*", "", "", ""
   "", "", "*Forcing*", ""
   "``formdrag``", "true/false", "calculate form drag", ""
   "``atmbndy``", "``default``", "stability-based boundary layer", "‘default’"
   "", "``constant``", "bulk transfer coefficients", ""
   "``fyear_init``", "yyyy", "first year of atmospheric forcing data", ""
   "``ycycle``", "integer", "number of years in forcing data cycle", ""
   "``atm_data_format``", "``nc``", "read  atmo forcing files", ""
   "", "``bin``", "read direct access, binary files", ""
   "``atm_data_type``", "``default``", "constant values defined in the code", ""
   "", "``LYq``", "AOMIP/Large-Yeager forcing data", ""
   "", "``monthly``", "monthly forcing data", ""
   "", "``ncar``", "NCAR bulk forcing data", ""
   "", "``oned``", "column forcing data", ""
   "``atm_data_dir``", "path/", "path to atmospheric forcing data directory", ""
   "``calc_strair``", "true", "calculate wind stress and speed", ""
   "", "false", "read wind stress and speed from files", ""
   "``highfreq``", "true/false", "high-frequency atmo coupling", ""
   "``natmiter``", "integer", "number of atmo boundary layer iterations", ""
   "``calc_Tsfc``", "true/false", "calculate surface temperature", "``.true.``"
   "``precip_units``", "``mks``", "liquid precipitation data units", ""
   "", "``mm_per_month``", "", ""
   "", "``mm_per_sec``", "(same as MKS units)", ""
   "``tfrz_option``", "``minus1p8``", "constant ocean freezing temperature (:math:`-1.8^{\circ} C`)", ""
   "", "``linear_salt``", "linear function of salinity (ktherm=1)", ""
   "", "``mushy_layer``", "matches mushy-layer thermo (ktherm=2)", ""
   "``ustar_min``", "real", "minimum value of ocean friction velocity", "0.0005 m/s"
   "``emissivity``", "real", "emissivity of snow and ice", "0.95"
   "``fbot_xfer_type``", "``constant``", "constant ocean heat transfer coefficient", ""
   "", "``Cdn_ocn``", "variable ocean heat transfer coefficient", ""
   "``update_ocn_f``", "true", "include frazil water/salt fluxes in ocn fluxes", ""
   "", "false", "do not include (when coupling with POP)", ""
   "``l_mpond_fresh``", "true", "retain (topo) pond water until ponds drain", ""
   "", "false", "release (topo) pond water immediately to ocean", ""
   "``oceanmixed_ice``", "true/false", "active ocean mixed layer calculation", "``.true.`` (if uncoupled)"
   "``ocn_data_format``", "``nc``", "read  ocean forcing files", ""
   "", "``bin``", "read direct access, binary files", ""
   "``sss_data_type``", "``default``", "constant values defined in the code", ""
   "", "``clim``", "climatological data", ""
   "", "``near``", "POP ocean forcing data", ""
   "``sst_data_type``", "``default``", "constant values defined in the code", ""
   "", "``clim``", "climatological data", ""
   "", "``ncar``", "POP ocean forcing data", ""
   "``ocn_data_dir``", "path/", "path to oceanic forcing data directory", ""
   "``oceanmixed_file``", "filename", "data file containing ocean forcing data", ""
   "``restore_sst``", "true/false", "restore sst to data", ""
   "``trestore``", "integer", "sst restoring time scale (days)", ""
   "``restore_ice``", "true/false", "restore ice state along lateral boundaries", ""
   "", "", "", ""
   "*icefields_tracer_nml*", "", "", ""
   "", "", "*History Fields*", ""
   "``f_<var>``", "string", "frequency units for writing ``<var>`` to history", ""
   "", "``y``", "write history every ``histfreq_n`` years", ""
   "", "``m``", "write history every ``histfreq_n`` months", ""
   "", "``d``", "write history every ``histfreq_n`` days", ""
   "", "``h``", "write history every ``histfreq_n`` hours", ""
   "", "``1``", "write history every time step", ""
   "", "``x``", "do not write ``<var>`` to history", ""
   "", "``md``", "*e.g.,* write both monthly and daily files", ""
   "``f_<var>_ai``", "", "grid cell average of ``<var>`` (:math:`\times a_i`)", ""


  
.. _tuning:

BGC Tuning Parameters
------------------------

Biogeochemical tuning parameters are specified as namelist options in
**ice\_in**. Table :ref:`tab-bio-tracers2` provides a list of parameters
used in the reaction equations, their representation in the code, a
short description of each and the default values. Please keep in mind
that there has only been minimal tuning of the model.

.. _tab-bio-tracers2:

.. csv-table:: *Biogeochemical Reaction Parameters*
   :header: "Text Variable", "Variable in code", "Description", "Value", "units"
   :widths: 7, 20, 15, 15, 15

   ":math:`f_{graze}`", "fr\_graze(1:3)", "fraction of growth grazed", "0, 0.1, 0.1", "1"
   ":math:`f_{res}`", "fr\_resp", "fraction of growth respired", "0.05", "1"
   ":math:`l_{max}`", "max\_loss", "maximum tracer loss fraction", "0.9", "1"
   ":math:`m_{pre}`", "mort\_pre(1:3)", "maximum mortality rate", "0.007, 0.007, 0.007", "day\ :math:`^{-1}`"
   ":math:`m_{T}`", "mort\_Tdep(1:3)", "mortality temperature decay", "0.03, 0.03, 0.03", ":math:`^o`\ C\ :math:`^{-1}`"
   ":math:`T_{max}`", "T\_max", "maximum brine temperature", "0", ":math:`^o`\ C"
   ":math:`k_{nitr}`", "k\_nitrif", "nitrification rate", "0", "day\ :math:`^{-1}`"
   ":math:`f_{ng}`", "fr\_graze\_e", "fraction of grazing excreted", "0.5", "1"
   ":math:`f_{gs}`", "fr\_graze\_s", "fraction of grazing spilled", "0.5", "1"
   ":math:`f_{nm}`", "fr\_mort2min", "fraction of mortality to :math:`{\mbox{NH$_4$}}`", "0.5", "1"
   ":math:`f_{dg}`", "f\_don", "frac. spilled grazing to :math:`{\mbox{DON}}`", "0.6", "1"
   ":math:`k_{nb}`", "kn\_bac :math:`^a`", "bacterial degradation of :math:`{\mbox{DON}}`", "0.03", "day\ :math:`^{-1}`"
   ":math:`f_{cg}`", "f\_doc(1:3)", "fraction of mortality to :math:`{\mbox{DOC}}`", "0.4, 0.4, 0.2 ", "1"
   ":math:`R_{c:n}^c`", "R\_C2N(1:3)", "algal carbon to nitrogen ratio", "7.0, 7.0, 7.0", "mol/mol"
   ":math:`k_{cb}`", "k\_bac1:3\ :math:`^a`", "bacterial degradation of DOC", "0.03, 0.03, 0.03", "day\ :math:`^{-1}`"
   ":math:`\tau_{fe}`", "t\_iron\_conv", "conversion time pFe :math:`\leftrightarrow` dFe", "3065.0 ", "day"
   ":math:`r^{max}_{fed:doc}`", "max\_dfe\_doc1", "max ratio of dFe to saccharids", "0.1852", "nM Fe\ :math:`/\mu`\ M C"
   ":math:`f_{fa}`", "fr\_dFe  ", "fraction of remin. N to dFe", "0.3", "1"
   ":math:`R_{fe:n}`", "R\_Fe2N(1:3)", "algal Fe to N ratio", "0.023, 0.023, 0.7", "mmol/mol"
   ":math:`R_{s:n}`", "R\_S2N(1:3)", "algal S to N ratio", "0.03, 0.03, 0.03", "mol/mol"
   ":math:`f_{sr}`", "fr\_resp\_s", "resp. loss as DMSPd", "0.75", "1"
   ":math:`\tau_{dmsp}`", "t\_sk\_conv", "Stefels rate", "3.0", "day"
   ":math:`\tau_{dms}`", "t\_sk\_ox", "DMS oxidation rate", "10.0", "day"
   ":math:`y_{dms}`", "y\_sk\_DMS", "yield for DMS conversion", "0.5", "1"
   ":math:`K_{{\mbox{NO$_3$}}}`", "K\_Nit(1:3)", ":math:`{\mbox{NO$_3$}}` half saturation constant", "1,1,1", "mmol/m\ :math:`^{3}`"
   ":math:`K_{{\mbox{NH$_4$}}}`", "K\_Am(1:3)", ":math:`{\mbox{NH$_4$}}` half saturation constant", "0.3, 0.3, 0.3", "mmol/m\ :math:`^{-3}`"
   ":math:`K_{{\mbox{SiO$_3$}}}`", "K\_Sil(1:3)", "silicate half saturation constant", "4.0, 0, 0", "mmol/m\ :math:`^{-3}`"
   ":math:`K_{{\mbox{fed}}}`", "K\_Fe(1:3)", "iron half saturation constant", "1.0, 0.2, 0.1", ":math:`\mu`\ mol/m\ :math:`^{-3}`"
   ":math:`op_{min}`", "op\_dep\_min", "boundary for light attenuation", "0.1", "1"
   ":math:`chlabs`", "chlabs(1:3)", "light absorption length per chla conc.", "0.03, 0.01, 0.05", "1\ :math:`/`\ m\ :math:`/`\ (mg\ :math:`/`\ m\ :math:`^{3}`)"
   ":math:`\alpha`", "alpha2max\_low(1:3)", "light limitation factor", "0.25, 0.25, 0.25", "m\ :math:`^2`/W"
   ":math:`\beta`", "beta2max(1:3)", "light inhibition factor", "0.018, 0.0025, 0.01", "m\ :math:`^2`/W"
   ":math:`\mu_{max}`", "mu\_max(1:3)", "maximum algal growth rate", "1.44, 0.851, 0.851", "day\ :math:`^{-1}`"
   ":math:`\mu_T`", "grow\_Tdep(1:3)", "temperature growth factor", "0.06, 0.06, 0.06", "day\ :math:`^{-1}`"
   ":math:`f_{sal}`", "fsal", "salinity growth factor", "1", "1"
   ":math:`R_{si:n}`", "R\_Si2N(1:3)", "algal silicate to nitrogen", "1.8, 0, 0", "mol/mol"

:math:`^a` only (1:2) of DOC and DOC parameters have physical meaning
