# utl-five-algorithms-for-a-simple-n-percent-crosstab
Five algorithms for a simple n percent crosstab 
    Five algorithms for a simple n percent crosstab                                                                                  
                                                                                                                                     
    github                                                                                                                           
    https://tinyurl.com/yafyt2jk                                                                                                     
    https://github.com/rogerjdeangelis/utl-five-algorithms-for-a-simple-n-percent-crosstab                                           
                                                                                                                                     
    This does colum percents                                                                                                         
                                                                                                                                     
    see for other examples                                                                                                           
    https://github.com/rogerjdeangelis?tab=repositories&q=clinical+report&type=&language=                                            
                                                                                                                                     
    https://tinyurl.com/yb3hqsnk                                                                                                     
    https://communities.sas.com/t5/SAS-Programming/Proc-Tabulate-Counts-and-Percentages-within-a-Single-Cell/m-p/664056              
                                                                                                                                     
         Alorithms                                                                                                                   
              a. complex proc report                                                                                                 
              b. sql                                                                                                                 
              c. proc corrresp                                                                                                       
              d. proc freq                                                                                                           
              e. fcmp and macro vars (based on Barts solution with minor changes)                                                    
                 Bartosz Jablonski                                                                                                   
                 yabwon@gmail.com                                                                                                    
              f. Unable to code  hash (HOH?)                                                                                         
    /*                   _                                                                                                           
    (_)_ __  _ __  _   _| |_                                                                                                         
    | | '_ \| '_ \| | | | __|                                                                                                        
    | | | | | |_) | |_| | |_                                                                                                         
    |_|_| |_| .__/ \__,_|\__|                                                                                                        
            |_|                                                                                                                      
    */                                                                                                                               
                                                                                                                                     
    data have;                                                                                                                       
      set sashelp.heart(keep=sex bp_status);                                                                                         
      output;                                                                                                                        
      sex="Total";                                                                                                                   
      output;                                                                                                                        
    run;quit;                                                                                                                        
                                                                                                                                     
                                                                                                                                     
     WORK.HAVE total obs=5,209                                                                                                       
                                                                                                                                     
        SEX      BP_STATUS                                                                                                           
                                                                                                                                     
       Female     Normal                                                                                                             
       Female     High                                                                                                               
       Female     High                                                                                                               
       Female     Normal                                                                                                             
       Male       Optimal                                                                                                            
       ...                                                                                                                           
                                                                                                                                     
    /*           _               _                                                                                                   
      ___  _   _| |_ _ __  _   _| |_ ___                                                                                             
     / _ \| | | | __| '_ \| | | | __/ __|                                                                                            
    | (_) | |_| | |_| |_) | |_| | |_\__ \                                                                                            
     \___/ \__,_|\__| .__/ \__,_|\__|___/                                                                                            
                    |_|                  _                                                                                           
      __ _     _ __ ___ _ __   ___  _ __| |_                                                                                         
     / _` |   | '__/ _ \ '_ \ / _ \| '__| __|                                                                                        
    | (_| |_  | | |  __/ |_) | (_) | |  | |_                                                                                         
     \__,_(_) |_|  \___| .__/ \___/|_|   \__|                                                                                        
                       |_|                                                                                                           
    */                                                                                                                               
                                                                                                                                     
    WORK.WANT total obs=3                                                                                                            
                                                                                                                                     
    Obs     SEX         HIGH_BP          NORMAL_BP        OPTIMAL_BP      ALL                                                        
                                                                                                                                     
     1     Total     2,267(100.00%)    2,143(100.00%)    799(100.00%)    5209                                                        
                                                                                                                                     
     2     Male      1,081(47.68%)     977(45.59%)       278(34.79%)     2336                                                        
     3     Female    1,186(52.32%)     1,166(54.41%)     521(65.21%)     2873                                                        
                                                                                                                                     
                                                                                                                                     
    /*                  _                                                                                                            
    | |__     ___  __ _| |                                                                                                           
    | '_ \   / __|/ _` | |                                                                                                           
    | |_) |  \__ \ (_| | |                                                                                                           
    |_.__(_) |___/\__, |_|                                                                                                           
                     |_|                                                                                                             
    */                                                                                                                               
                                                                                                                                     
    Up to 40 obs WORK.WANT total obs=3                                                                                               
                                                                                                                                     
    Obs     SEX      _NAME_       HIGH         NORMAL       OPTIMAL                                                                  
                                                                                                                                     
     1     Total      NPCT     2267(100%)    2143(100%)    799(100%)                                                                 
     2     Male       NPCT     1081(48%)     977(46%)      278(35%)                                                                  
     3     Female     NPCT     1186(52%)     1166(54%)     521(65%)                                                                  
                                                                                                                                     
    /*                                                                                                                               
      ___      ___ ___  _ __ _ __ ___  ___ _ __                                                                                      
     / __|    / __/ _ \| '__| '__/ _ \/ __| '_ \                                                                                     
    | (__ _  | (_| (_) | |  | | |  __/\__ \ |_) |                                                                                    
     \___(_)  \___\___/|_|  |_|  \___||___/ .__/                                                                                     
                                          |_|                                                                                        
    */                                                                                                                               
                                                                                                                                     
     WORK.WANT total obs=3                                                                                                           
                                                                                                                                     
                                                  OPTIMAL_                                                                           
      SEX       HIGH_NPCT        NORMAL_NPCT      NPCT                                                                               
                                                                                                                                     
      Female    1,186(52.32%)    1,166(54.41%)    521(65.21%)                                                                        
      Male      1,081(47.68%)    977(45.59%)      278(34.79%)                                                                        
      Sum       2,267            2,143            799                                                                                
                                                                                                                                     
    /*   _      __                                                                                                                   
      __| |    / _|_ __ ___  __ _                                                                                                    
     / _` |   | |_| '__/ _ \/ _` |                                                                                                   
    | (_| |_  |  _| | |  __/ (_| |                                                                                                   
     \__,_(_) |_| |_|  \___|\__, |                                                                                                   
                               |_|                                                                                                   
    */                                                                                                                               
                                                                                                                                     
     WORK.WANT total obs=3                                                                                                           
                                                                                                                                     
                                                  OPTIMAL_                                                                           
      LEVEL     HIGH_NPCT        NORMAL_NPCT      NPCT                                                                               
                                                                                                                                     
      Female    1,186(52.32%)    1,166(54.41%)    521(65.21%)                                                                        
      Male      1,081(47.68%)    977(45.59%)      278(34.79%)                                                                        
      Sum       2267             2143             799                                                                                
                                                                                                                                     
    /*         __                                                                                                                    
      ___     / _| ___ _ __ ___  _ __                                                                                                
     / _ \   | |_ / __| '_ ` _ \| '_ \                                                                                               
    |  __/_  |  _| (__| | | | | | |_) |                                                                                              
     \___(_) |_|  \___|_| |_| |_| .__/                                                                                               
                                |_|                                                                                                  
    */                                                                                                                               
                                                                                                                                     
    Up to 40 obs WORK.WANT total obs=3                                                                                               
                                                                                                                                     
    Obs    Sex           HIGH_B  P           NORMAL_BP        OPTIMAL_BP       ALL                                                   
                                                                                                                                     
     1     Female    1,186 (52.32%)     1,166 (54.41%)     521 (65.21%)     2873                                                     
     2     Male      1,081 (47.68%)     977 (45.59%)       278 (34.79%)     2336                                                     
     3     Tot       2,267 (100.00%)    2,143 (100.00%)    799 (100.00%)    5209                                                     
                                                                                                                                     
    /*         _       _   _                                                                                                         
     ___  ___ | |_   _| |_(_) ___  _ __  ___                                                                                         
    / __|/ _ \| | | | | __| |/ _ \| '_ \/ __|                                                                                        
    \__ \ (_) | | |_| | |_| | (_) | | | \__ \                                                                                        
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|___/                                                                                        
                                         _                                                                                           
      __ _     _ __ ___ _ __   ___  _ __| |_                                                                                         
     / _` |   | '__/ _ \ '_ \ / _ \| '__| __|                                                                                        
    | (_| |_  | | |  __/ |_) | (_) | |  | |_                                                                                         
     \__,_(_) |_|  \___| .__/ \___/|_|   \__|                                                                                        
                       |_|                                                                                                           
    */                                                                                                                               
                                                                                                                                     
    proc report data=have(keep=sex bp_status) nowd                                                                                   
              out=want_RPT (where=(sex ne '') keep=sex high_bp normal_bp optimal_bp all) ;                                           
                                                                                                                                     
       column sex bp_status, (n pct) high_bp normal_bp optimal_bp all;                                                               
                                                                                                                                     
       define sex / group descending;                                                                                                
       define bp_status / across;                                                                                                    
       define n   / noprint;                                                                                                         
       define pct / computed noprint ;                                                                                               
                                                                                                                                     
       define high_bp /computed "high_bp"     format=$18.;                                                                           
       define normal_bp /computed "normal_bp"   format=$18.;                                                                         
       define optimal_bp /computed "optimal_bp"  format=$18.;                                                                        
                                                                                                                                     
       define all  /computed "total"      format=comma12.;                                                                           
                                                                                                                                     
       /* sum total number of responses to question */                                                                               
       compute before;                                                                                                               
          denom3 = _c2_;                                                                                                             
          denom5 = _c4_;                                                                                                             
          denom7 = _c6_;                                                                                                             
       endcomp;                                                                                                                      
                                                                                                                                     
       /* calculate percentage */                                                                                                    
       compute pct;                                                                                                                  
          _c3_ = _c2_ / denom3;                                                                                                      
          _c5_ = _c4_ / denom5;                                                                                                      
          _c7_ = _c6_ / denom7;                                                                                                      
       endcomp;                                                                                                                      
                                                                                                                                     
       compute all;                                                                                                                  
          all = (_c2_ + _c4_ + _c6_);                                                                                                
       endcomp;                                                                                                                      
                                                                                                                                     
       compute high_bp/character;high_bp=cats(put(_c2_,comma12.),'(',put(200*_c2_/ denom3,7.2),'%)');endcomp;                        
       compute normal_bp/character;normal_bp=cats(put(_c4_,comma12.),'(',put(200*_c4_/ denom5,7.2),'%)');endcomp;                    
       compute optimal_bp/character;optimal_bp=cats(put(_c6_,comma12.),'(',put(200*_c6_/ denom7,7.2),'%)');endcomp;                  
                                                                                                                                     
    run;quit;                                                                                                                        
    /*                  _                                                                                                            
    | |__     ___  __ _| |                                                                                                           
    | '_ \   / __|/ _` | |                                                                                                           
    | |_) |  \__ \ (_| | |                                                                                                           
    |_.__(_) |___/\__, |_|                                                                                                           
                     |_|                                                                                                             
    */                                                                                                                               
                                                                                                                                     
    proc sql;                                                                                                                        
       create                                                                                                                        
         table prewant as                                                                                                            
       select                                                                                                                        
        distinct                                                                                                                     
         l.bp_status                                                                                                                 
        ,l.sex                                                                                                                       
        ,count(l.bp_status) as cntbp                                                                                                 
        ,r.cntgrp                                                                                                                    
        ,cats(put(count(l.bp_status),4.),'(',put(2*count(l.bp_status)/r.cntgrp,percent.),')') as npct                                
      from                                                                                                                           
         have as l, (select bp_status,count(bp_status) as cntgrp from have group by bp_status) as r                                  
      where                                                                                                                          
         l.bp_status       =  r.bp_status                                                                                            
      group                                                                                                                          
         by l.bp_status, l.sex                                                                                                       
      order                                                                                                                          
         by l.sex descending, bp_status                                                                                              
                                                                                                                                     
    ;quit;                                                                                                                           
                                                                                                                                     
    proc transpose data=prewant out=want_SQL;                                                                                        
    by sex notsorted;                                                                                                                
    id bp_status;                                                                                                                    
    var npct;                                                                                                                        
    run;quit;                                                                                                                        
                                                                                                                                     
    /*                                                                                                                               
      ___      ___ ___  _ __ _ __ ___  ___ _ __                                                                                      
     / __|    / __/ _ \| '__| '__/ _ \/ __| '_ \                                                                                     
    | (__ _  | (_| (_) | |  | | |  __/\__ \ |_) |                                                                                    
     \___(_)  \___\___/|_|  |_|  \___||___/ .__/                                                                                     
                                          |_|                                                                                        
    */                                                                                                                               
                                                                                                                                     
                                                                                                                                     
    Ods exclude All;                                                                                                                 
    Ods Output Observed=havcnt(Rename=Label=sex);                                                                                    
    ods output colprofiles=havColPct(rename=(label=Sex));                                                                            
    Proc Corresp Data=have(where=(sex ne 'Total')) all Observed dim=1 print=both;                                                    
       Table sex, bp_status;                                                                                                         
    Run;                                                                                                                             
    Ods Select All;                                                                                                                  
                                                                                                                                     
    data want_COR(where=(sex ne 'Sum'));                                                                                             
      merge havCnt havColpct(rename=(high=_high normal=_normal optimal=_optimal));                                                   
      select (sex);                                                                                                                  
          when ('Sum') do;                                                                                                           
             high_npct    = cats(put(high,comma12.));                                                                                
             normal_npct  = cats(put(normal,comma12.));                                                                              
             optimal_npct = cats(put(optimal,comma12.));                                                                             
          end;                                                                                                                       
          otherwise do;                                                                                                              
             high_npct    = cats(put(high,comma12.)   ,'(',put(200*_high,7.2),'%)');                                                 
             normal_npct  = cats(put(normal,comma12.) ,'(',put(200*_normal,7.2),'%)');                                               
             optimal_npct = cats(put(optimal,comma12.),'(',put(200*_optimal,7.2),'%)');                                              
          end;                                                                                                                       
      end;                                                                                                                           
      keep sex high_npct normal_npct optimal_npct ;                                                                                  
    run;quit;                                                                                                                        
                                                                                                                                     
                                                                                                                                     
    /*   _      __                                                                                                                   
      __| |    / _|_ __ ___  __ _                                                                                                    
     / _` |   | |_| '__/ _ \/ _` |                                                                                                   
    | (_| |_  |  _| | |  __/ (_| |                                                                                                   
     \__,_(_) |_| |_|  \___|\__, |                                                                                                   
                               |_|                                                                                                   
    */                                                                                                                               
                                                                                                                                     
    options sasautos=(sasautos "c:/oto");                                                                                            
    %utl_odsfrq(setup);                                                                                                              
    proc freq data=have(where=(sex ne 'Total'));                                                                                     
    tables sex*bp_status;                                                                                                            
    run;quit;                                                                                                                        
    %utl_odsfrq(outdsn=xtab);                                                                                                        
                                                                                                                                     
    data want-FRQ;                                                                                                                   
      retain level;                                                                                                                  
      retain h n o 0;                                                                                                                
      length                                                                                                                         
          HIGH_NPCT                                                                                                                  
          NORMAL_NPCT                                                                                                                
          ORDINAL_NPCT $18                                                                                                           
      ;                                                                                                                              
      merge xtab(where=(upcase(rownam)="COUNT"                                                                                       
      )) xtab(where=(upcase(rownam)="COL PCT") rename=(high=_high normal=_normal optimal=_optimal)) end=dne;                         
                                                                                                                                     
      high_npct    = cats(put(high,comma12.)   ,'(',put(_high,7.2),'%)');                                                            
      normal_npct  = cats(put(normal,comma12.) ,'(',put(_normal,7.2),'%)');                                                          
      optimal_npct = cats(put(optimal,comma12.),'(',put(_optimal,7.2),'%)');                                                         
                                                                                                                                     
      h=sum(h,high);                                                                                                                 
      n=sum(n,normal);                                                                                                               
      o=sum(o,optimal);                                                                                                              
      output;                                                                                                                        
                                                                                                                                     
      if dne then do;                                                                                                                
        level="Sum";                                                                                                                 
        HIGH_NPCT    = cats(h);                                                                                                      
        NORMAL_NPCT  = cats(n);                                                                                                      
        optimal_NPCT = cats(o);                                                                                                      
        output;                                                                                                                      
      end;                                                                                                                           
                                                                                                                                     
      keep level high_npct normal_npct optimal_npct;                                                                                 
                                                                                                                                     
    run;quit;                                                                                                                        
                                                                                                                                     
                                                                                                                                     
    /*         __                                                                                                                    
      ___     / _| ___ _ __ ___  _ __                                                                                                
     / _ \   | |_ / __| '_ ` _ \| '_ \                                                                                               
    |  __/_  |  _| (__| | | | | | |_) |                                                                                              
     \___(_) |_|  \___|_| |_| |_| .__/                                                                                               
                                |_|                                                                                                  
    */                                                                                                                               
                                                                                                                                     
    * I remember a discussuin years ago with Ian Whitlock about                                                                      
      using macro lookups. The feeling was that it is                                                                                
      faster than formats. Macro variables are n memory.;                                                                            
                                                                                                                                     
    *  Perhaps the code is easier to maintain;                                                                                       
                                                                                                                                     
    data have;                                                                                                                       
      set sashelp.heart(keep=sex bp_status);                                                                                         
      output;                                                                                                                        
      sex="Tot";                                                                                                                     
      output;                                                                                                                        
    run;                                                                                                                             
                                                                                                                                     
                                                                                                                                     
    proc fcmp outlib = work.f.p;                                                                                                     
      function summary(n,d) $ 60;                                                                                                    
        length result $ 60;                                                                                                          
                                                                                                                                     
        result = catx(" ", put(n, comma12.0) , cats("(", put(divide(n,d), percent12.2),")") );                                       
        return (result);                                                                                                             
      endsub;                                                                                                                        
    run;                                                                                                                             
                                                                                                                                     
    options cmplib = work.f;                                                                                                         
                                                                                                                                     
    %let  Female =1;                                                                                                                 
    %let  Male   =2;                                                                                                                 
    %let  Tot    =3;                                                                                                                 
                                                                                                                                     
    %let  High   =1;                                                                                                                 
    %let  Normal =2;                                                                                                                 
    %let  Optimal=3;                                                                                                                 
                                                                                                                                     
    options validvarname=v7;                                                                                                         
                                                                                                                                     
    data want;                                                                                                                       
                                                                                                                                     
      do until(eof);                                                                                                                 
                                                                                                                                     
        set have end = eof;                                                                                                          
        array sex_by_bp[3,0:3] _temporary_;                                                                                          
        array BP[3] $ 32 HIGH_BP NORMAL_BP OPTIMAL_BP;                                                                               
                                                                                                                                     
        sex_by_bp[symgetn(sex),symgetn(bp_status)] + 1;                                                                              
        sex_by_bp[symgetn(sex),0] + 1;                                                                                               
                                                                                                                                     
      end;                                                                                                                           
                                                                                                                                     
      do sex = "Female", "Male", "Tot";                                                                                              
        ALL = sex_by_bp[symgetn(sex),0];                                                                                             
        do j=&High, &Normal, &Optimal;                                                                                               
          BP[j] = summary(sex_by_bp[symgetn(sex),j], sex_by_bp[3,j]);                                                                
        end;                                                                                                                         
        output;                                                                                                                      
      end;                                                                                                                           
    stop;                                                                                                                            
    keep SEX HIGH_BP NORMAL_BP OPTIMAL_BP ALL;                                                                                       
    run;                                                                                                                             
                                                                                                                                     
                                                                                                                                     
                                                                                                                                     
    Up to 40 obs WORK.WANT total obs=3                                                                                               
                                                                                                                                     
    Obs    Sex           HIGH_B  P           NORMAL_BP        OPTIMAL_BP       ALL                                                   
                                                                                                                                     
     1     Female    1,186 (52.32%)     1,166 (54.41%)     521 (65.21%)     2873                                                     
     2     Male      1,081 (47.68%)     977 (45.59%)       278 (34.79%)     2336                                                     
     3     Tot       2,267 (100.00%)    2,143 (100.00%)    799 (100.00%)    5209                                                     
                                                                                                                                     
