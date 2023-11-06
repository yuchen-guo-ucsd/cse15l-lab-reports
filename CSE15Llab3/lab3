# CSE 15L Lab Report 3
## Yuchen Guo
### Part1

Failure-inducing input
```
@Test 
	public void testFiles1() throws IOException {
        File input = new File("some-files/");
        List<File> inputResult = FileExample.getFiles(input);
        List<File> result = new ArrayList<>();
        result.add(new File("some-files/a.txt"));
        result.add(new File("some-files/more-files/b.txt"));
        result.add(new File("some-files/more-files/c.java"));
        result.add(new File("some-files/even-more-files/a.txt"));
        result.add(new File("some-files/even-more-files/d.java"));
        
        
        assertEquals(result, inputResult);
    }
```
Success input
```
@Test 
	public void testFiles2() throws IOException {
        File input = new File("some-files/a.txt");
        List<File> inputResult = FileExample.getFiles(input);
        List<File> result = new ArrayList<>();
        result.add(new File("some-files/a.txt"));
        
        assertEquals(result, inputResult);
    }
```
Symptoms
![Image](junitoutput.png)

Bugs
```
import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

public class FileExample {
static List<File> getFiles(File start) throws IOException {
	  File f = start;
	  List<File> result = new ArrayList<>();
	  result.add(start);
	  if(f.isDirectory()) {
	    File[] paths = f.listFiles();
	    for(File subFile: paths) {
	      result.add(subFile);
	    }
	  }
	  return result;
	}
}
```
Bug-fixed
```
import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

public class FileExample {
  static List<File> getFiles(File start) throws IOException {
	  File f = start;
	  List<File> result = new ArrayList<>();
    findAllfiles(f, result);
    return result;
  }
	  
  static void findAllfiles(File file, List<File> result){
    if(file.isDirectory()) {
	    File[] paths = file.listFiles();
	    for(File subfile: paths) {
        findAllfiles(subfile, result);
             }
            }       
    else if(file.isFile()){
          result.add(0,file);
        }    
  }
}
```
I added a findAllfiles to recursively find all the files in the given path and its subdirectories since it was only showing the file path and the one step down in the directory (only first level of subdirectories). After fixing it, it perform as expected to go all the way down and find the files and reture files paths when given the input path.

### Part2

```
hogan@Hogans-MacBook-Air technical % find plos/ -size +30k
plos//pmed.0020059.txt
plos//pmed.0020073.txt
plos//pmed.0020249.txt
plos//pmed.0020103.txt
plos//pmed.0010028.txt
plos//pmed.0020018.txt
plos//pmed.0020182.txt
plos//pmed.0020246.txt
plos//pmed.0020045.txt
plos//pmed.0010036.txt
hogan@Hogans-MacBook-Air technical % 

```
It finds all files with the size that are greater than 30kb in plos/ folder. It is useful when users try to find large-size files.
Reference:https://man7.org/linux/man-pages/man1/find.1.html

```
hogan@Hogans-MacBook-Air technical % find plos/ -size -1k  
plos//pmed.0020191.txt
plos//pmed.0020226.txt
hogan@Hogans-MacBook-Air technical % 
```
It finds all files with the size that are less than 1kb in plos/ folder. It is useful when users try to find really small files.
Reference:https://man7.org/linux/man-pages/man1/find.1.html

```
hogan@Hogans-MacBook-Air technical % find plos/ -mtime +3 
plos/
plos//pmed.0020273.txt
plos//journal.pbio.0030032.txt
plos//pmed.0020065.txt
plos//pmed.0020071.txt
plos//pmed.0020059.txt
plos//pmed.0010039.txt
plos//journal.pbio.0020354.txt
plos//pmed.0010010.txt
plos//journal.pbio.0020156.txt
plos//pmed.0020104.txt
plos//pmed.0020272.txt
plos//pmed.0020258.txt
plos//pmed.0020099.txt
plos//journal.pbio.0020140.txt
plos//journal.pbio.0020183.txt
plos//journal.pbio.0020430.txt
plos//journal.pbio.0020394.txt
plos//journal.pbio.0020431.txt
plos//journal.pbio.0020419.txt
plos//pmed.0010013.txt
plos//pmed.0020113.txt
plos//journal.pbio.0020169.txt
plos//pmed.0020098.txt
plos//journal.pbio.0020035.txt
plos//pmed.0020067.txt
plos//pmed.0020073.txt
plos//journal.pbio.0030024.txt
plos//journal.pbio.0020223.txt
plos//pmed.0020249.txt
plos//pmed.0020275.txt
plos//journal.pbio.0020019.txt
plos//pmed.0020088.txt
plos//journal.pbio.0020145.txt
plos//pmed.0020103.txt
plos//pmed.0020117.txt
plos//journal.pbio.0020353.txt
plos//journal.pbio.0020347.txt
plos//journal.pbio.0020420.txt
plos//journal.pbio.0020346.txt
plos//journal.pbio.0020187.txt
plos//pmed.0020116.txt
plos//pmed.0020102.txt
plos//journal.pbio.0020150.txt
plos//pmed.0020062.txt
plos//pmed.0020274.txt
plos//journal.pbio.0020232.txt
plos//journal.pbio.0030021.txt
plos//journal.pbio.0020224.txt
plos//pmed.0020048.txt
plos//pmed.0020060.txt
plos//pmed.0020074.txt
plos//journal.pbio.0020146.txt
plos//pmed.0020114.txt
plos//pmed.0010028.txt
plos//journal.pbio.0020350.txt
plos//journal.pbio.0020190.txt
plos//pmed.0010029.txt
plos//pmed.0020115.txt
plos//journal.pbio.0020147.txt
plos//pmed.0020075.txt
plos//pmed.0020061.txt
plos//pmed.0020210.txt
plos//pmed.0020238.txt
plos//journal.pbio.0030051.txt
plos//journal.pbio.0020068.txt
plos//journal.pbio.0020054.txt
plos//journal.pbio.0020040.txt
plos//pmed.0010066.txt
plos//journal.pbio.0030131.txt
plos//journal.pbio.0020337.txt
plos//pmed.0020198.txt
plos//pmed.0010067.txt
plos//journal.pbio.0020121.txt
plos//pmed.0020007.txt
plos//journal.pbio.0030050.txt
plos//pmed.0020239.txt
plos//journal.pbio.0020241.txt
plos//pmed.0020005.txt
plos//journal.pbio.0020043.txt
plos//pmed.0020039.txt
plos//pmed.0010071.txt
plos//journal.pbio.0030127.txt
plos//pmed.0010058.txt
plos//pmed.0010070.txt
plos//pmed.0010064.txt
plos//pmed.0020158.txt
plos//journal.pbio.0020042.txt
plos//journal.pbio.0020297.txt
plos//pmed.0020206.txt
plos//pmed.0020212.txt
plos//pmed.0020216.txt
plos//journal.pbio.0030094.txt
plos//journal.pbio.0020046.txt
plos//pmed.0020028.txt
plos//journal.pbio.0020052.txt
plos//pmed.0020148.txt
plos//pmed.0020160.txt
plos//pmed.0010048.txt
plos//pmed.0010060.txt
plos//journal.pbio.0030137.txt
plos//journal.pbio.0030136.txt
plos//pmed.0010061.txt
plos//pmed.0010049.txt
plos//pmed.0020161.txt
plos//journal.pbio.0020127.txt
plos//pmed.0020149.txt
plos//journal.pbio.0020133.txt
plos//pmed.0020015.txt
plos//journal.pbio.0020053.txt
plos//journal.pbio.0020047.txt
plos//pmed.0020203.txt
plos//journal.pbio.0030056.txt
plos//pmed.0020201.txt
plos//journal.pbio.0030097.txt
plos//pmed.0020017.txt
plos//journal.pbio.0020125.txt
plos//journal.pbio.0020440.txt
plos//pmed.0010062.txt
plos//pmed.0020189.txt
plos//pmed.0020162.txt
plos//pmed.0020016.txt
plos//pmed.0020002.txt
plos//pmed.0020200.txt
plos//pmed.0020231.txt
plos//journal.pbio.0020263.txt
plos//pmed.0020027.txt
plos//pmed.0020033.txt
plos//journal.pbio.0020101.txt
plos//pmed.0010047.txt
plos//journal.pbio.0030105.txt
plos//journal.pbio.0020302.txt
plos//pmed.0010046.txt
plos//pmed.0010052.txt
plos//pmed.0020191.txt
plos//journal.pbio.0020100.txt
plos//pmed.0020146.txt
plos//journal.pbio.0020262.txt
plos//journal.pbio.0030065.txt
plos//journal.pbio.0020276.txt
plos//pmed.0020232.txt
plos//pmed.0020226.txt
plos//pmed.0020024.txt
plos//pmed.0020018.txt
plos//pmed.0020144.txt
plos//pmed.0020150.txt
plos//journal.pbio.0020116.txt
plos//pmed.0020187.txt
plos//pmed.0010050.txt
plos//pmed.0010051.txt
plos//pmed.0020192.txt
plos//pmed.0010045.txt
plos//pmed.0020145.txt
plos//pmed.0020019.txt
plos//journal.pbio.0020063.txt
plos//journal.pbio.0030076.txt
plos//journal.pbio.0030062.txt
plos//pmed.0020237.txt
plos//journal.pbio.0020067.txt
plos//pmed.0020009.txt
plos//journal.pbio.0020073.txt
plos//pmed.0020035.txt
plos//pmed.0020021.txt
plos//journal.pbio.0020113.txt
plos//pmed.0020155.txt
plos//pmed.0010069.txt
plos//pmed.0010041.txt
plos//pmed.0020182.txt
plos//pmed.0020196.txt
plos//journal.pbio.0020311.txt
plos//journal.pbio.0030102.txt
plos//journal.pbio.0020310.txt
plos//pmed.0020197.txt
plos//pmed.0010068.txt
plos//pmed.0020140.txt
plos//journal.pbio.0020112.txt
plos//pmed.0020020.txt
plos//pmed.0020034.txt
plos//pmed.0020236.txt
plos//journal.pbio.0020272.txt
plos//pmed.0020208.txt
plos//journal.pbio.0020064.txt
plos//pmed.0020022.txt
plos//pmed.0020036.txt
plos//pmed.0010056.txt
plos//pmed.0020195.txt
plos//pmed.0010042.txt
plos//pmed.0020181.txt
plos//journal.pbio.0020306.txt
plos//journal.pbio.0030129.txt
plos//journal.pbio.0020307.txt
plos//pmed.0020180.txt
plos//pmed.0020194.txt
plos//pmed.0020157.txt
plos//journal.pbio.0020105.txt
plos//pmed.0020023.txt
plos//journal.pbio.0020071.txt
plos//pmed.0020235.txt
plos//journal.pbio.0020267.txt
plos//pmed.0020209.txt
plos//pmed.0020246.txt
plos//journal.pbio.0020228.txt
plos//journal.pbio.0020214.txt
plos//pmed.0020050.txt
plos//pmed.0020118.txt
plos//pmed.0010030.txt
plos//pmed.0010024.txt
plos//journal.pbio.0020348.txt
plos//journal.pbio.0020406.txt
plos//pmed.0010025.txt
plos//pmed.0020086.txt
plos//pmed.0020045.txt
plos//journal.pbio.0020215.txt
plos//pmed.0020247.txt
plos//pmed.0020047.txt
plos//journal.pbio.0020001.txt
plos//pmed.0020090.txt
plos//journal.pbio.0020161.txt
plos//journal.pbio.0020439.txt
plos//journal.pbio.0020404.txt
plos//pmed.0010026.txt
plos//journal.pbio.0020148.txt
plos//pmed.0020085.txt
plos//pmed.0020091.txt
plos//journal.pbio.0020028.txt
plos//journal.pbio.0020216.txt
plos//pmed.0020278.txt
plos//pmed.0020268.txt
plos//journal.pbio.0020206.txt
plos//journal.pbio.0020010.txt
plos//journal.pbio.0020164.txt
plos//pmed.0010022.txt
plos//pmed.0010036.txt
plos//journal.pbio.0020400.txt
plos//journal.pbio.0020401.txt
plos//pmed.0010023.txt
plos//pmed.0020123.txt
plos//pmed.0020094.txt
plos//journal.pbio.0020213.txt
plos//pmed.0020257.txt
plos//journal.pbio.0020013.txt
plos//pmed.0020055.txt
plos//pmed.0020082.txt
plos//pmed.0010021.txt
plos//pmed.0010034.txt
plos//pmed.0010008.txt
plos//pmed.0020120.txt
plos//journal.pbio.0020172.txt
plos//pmed.0020040.txt
plos//pmed.0020068.txt
plos//journal.pbio.0020012.txt
plos//pmed.0020281.txt
plos//pmed.0020242.txt
hogan@Hogans-MacBook-Air technical % 
```
This command shows the file that was edit or modified more than 3 days in plos/ folder. It's useful when trying to find a file that based on the time it was modified. 
Reference:https://man7.org/linux/man-pages/man1/find.1.html

```
hogan@Hogans-MacBook-Air technical % find plos/ -mtime -1 
plos/
plos//journal.pbio.0020001.txt
hogan@Hogans-MacBook-Air technical % 

```
This shows the file that was modified within 1 day in plos/ folder, so users could find the recent files that was modified today.
Reference:https://man7.org/linux/man-pages/man1/find.1.html

```
hogan@Hogans-MacBook-Air technical % find government/ -type f 
government//About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
government//About_LSC/Progress_report.txt
government//About_LSC/Strategic_report.txt
government//About_LSC/Comments_on_semiannual.txt
government//About_LSC/Special_report_to_congress.txt
government//About_LSC/CONFIG_STANDARDS.txt
government//About_LSC/commission_report.txt
government//About_LSC/LegalServCorp_v_VelazquezDissent.txt
government//About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
government//About_LSC/LegalServCorp_v_VelazquezOpinion.txt
government//About_LSC/diversity_priorities.txt
government//About_LSC/reporting_system.txt
government//About_LSC/State_Planning_Report.txt
government//About_LSC/Protocol_Regarding_Access.txt
government//About_LSC/ODonnell_et_al_v_LSCdecision.txt
government//About_LSC/conference_highlights.txt
government//About_LSC/State_Planning_Special_Report.txt
government//Env_Prot_Agen/multi102902.txt
government//Env_Prot_Agen/section-by-section_summary.txt
government//Env_Prot_Agen/jeffordslieberm.txt
government//Env_Prot_Agen/final.txt
government//Env_Prot_Agen/ctf7-10.txt
government//Env_Prot_Agen/ctf1-6.txt
government//Env_Prot_Agen/ro_clear_skies_book.txt
government//Env_Prot_Agen/ctm4-10.txt
government//Env_Prot_Agen/1-3_meth_901.txt
government//Env_Prot_Agen/atx1-6.txt
government//Env_Prot_Agen/tech_sectiong.txt
government//Env_Prot_Agen/bill.txt
government//Env_Prot_Agen/nov1.txt
government//Env_Prot_Agen/tech_adden.txt
government//Alcohol_Problems/Session2-PDF.txt
government//Alcohol_Problems/Session3-PDF.txt
government//Alcohol_Problems/DraftRecom-PDF.txt
government//Alcohol_Problems/Session4-PDF.txt
government//Gen_Account_Office/d0269g.txt
government//Gen_Account_Office/Testimony_cg00010t.txt
government//Gen_Account_Office/og97032.txt
government//Gen_Account_Office/og99036.txt
government//Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
government//Gen_Account_Office/Sept27-2002_d02966.txt
government//Gen_Account_Office/d01376g.txt
government//Gen_Account_Office/Statements_Feb28-1997_volume.txt
government//Gen_Account_Office/og97019.txt
government//Gen_Account_Office/pe1019.txt
government//Gen_Account_Office/Testimony_Jul15-2002_d02940t.txt
government//Gen_Account_Office/gg96118.txt
government//Gen_Account_Office/og97020.txt
government//Gen_Account_Office/ffm.txt
government//Gen_Account_Office/og97023.txt
government//Gen_Account_Office/July11-2001_gg00172r.txt
government//Gen_Account_Office/d01121g.txt
government//Gen_Account_Office/og96011.txt
government//Gen_Account_Office/d03419sp.txt
government//Gen_Account_Office/Letter_Walkeraug17let.txt
government//Gen_Account_Office/og97051.txt
government//Gen_Account_Office/og97045.txt
government//Gen_Account_Office/Testimony_d01609t.txt
government//Gen_Account_Office/og97050.txt
government//Gen_Account_Office/og96038.txt
government//Gen_Account_Office/og98029.txt
government//Gen_Account_Office/Sept14-2002_d011070.txt
government//Gen_Account_Office/d03273g.txt
government//Gen_Account_Office/Oct15-1999_gg00026t.txt
government//Gen_Account_Office/og96012.txt
government//Gen_Account_Office/og97046.txt
government//Gen_Account_Office/og97052.txt
government//Gen_Account_Office/d03232sp.txt
government//Gen_Account_Office/og97043.txt
government//Gen_Account_Office/June30-2000_gg00135r.txt
government//Gen_Account_Office/d01591sp.txt
government//Gen_Account_Office/Oct15-2001_d0224.txt
government//Gen_Account_Office/og96028.txt
government//Gen_Account_Office/og96014.txt
government//Gen_Account_Office/og97041.txt
government//Gen_Account_Office/og96015.txt
government//Gen_Account_Office/d01145g.txt
government//Gen_Account_Office/InternalControl_ai00021p.txt
government//Gen_Account_Office/og96031.txt
government//Gen_Account_Office/d01186g.txt
government//Gen_Account_Office/og96033.txt
government//Gen_Account_Office/og96027.txt
government//Gen_Account_Office/og98022.txt
government//Gen_Account_Office/og96026.txt
government//Gen_Account_Office/og96032.txt
government//Gen_Account_Office/im814.txt
government//Gen_Account_Office/og96036.txt
government//Gen_Account_Office/og96022.txt
government//Gen_Account_Office/og96023.txt
government//Gen_Account_Office/og96037.txt
government//Gen_Account_Office/og98032.txt
government//Gen_Account_Office/og98026.txt
government//Gen_Account_Office/og98030.txt
government//Gen_Account_Office/og98024.txt
government//Gen_Account_Office/og96009.txt
government//Gen_Account_Office/og96021.txt
government//Gen_Account_Office/og98018.txt
government//Gen_Account_Office/ai00134.txt
government//Gen_Account_Office/og96034.txt
government//Gen_Account_Office/og98019.txt
government//Gen_Account_Office/og96020.txt
government//Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt
government//Gen_Account_Office/og96047.txt
government//Gen_Account_Office/ai9868.txt
government//Gen_Account_Office/og98041.txt
government//Gen_Account_Office/og97038.txt
government//Gen_Account_Office/Paper_Walker11-2002_acpro122.txt
government//Gen_Account_Office/og97011.txt
government//Gen_Account_Office/og97039.txt
government//Gen_Account_Office/May1998_ai98068.txt
government//Gen_Account_Office/og98040.txt
government//Gen_Account_Office/og96045.txt
government//Gen_Account_Office/og98044.txt
government//Gen_Account_Office/og96041.txt
government//Gen_Account_Office/d02701.txt
government//Gen_Account_Office/og97001.txt
government//Gen_Account_Office/og97028.txt
government//Gen_Account_Office/ai2132.txt
government//Gen_Account_Office/Letter_WalkerJan30-2001.txt
government//Gen_Account_Office/og96040.txt
government//Gen_Account_Office/og98045.txt
government//Gen_Account_Office/og96042.txt
government//Gen_Account_Office/og97002.txt
government//Gen_Account_Office/og97003.txt
government//Gen_Account_Office/og96043.txt
government//Gen_Account_Office/og98046.txt
government//Post_Rate_Comm/Gleiman_EMASpeech.txt
government//Post_Rate_Comm/Mitchell_spyros-first-class.txt
government//Post_Rate_Comm/Cohenetal_CreamSkimming.txt
government//Post_Rate_Comm/Cohenetal_DeliveryCost.txt
government//Post_Rate_Comm/Mitchell_RMVancouver.txt
government//Post_Rate_Comm/Gleiman_gca2000.txt
government//Post_Rate_Comm/Cohenetal_Cost_Function.txt
government//Post_Rate_Comm/Redacted_Study.txt
government//Post_Rate_Comm/Mitchell_6-17-Mit.txt
government//Post_Rate_Comm/Cohenetal_comparison.txt
government//Post_Rate_Comm/Cohenetal_Scale.txt
government//Post_Rate_Comm/Cohenetal_RuralDelivery.txt
government//Post_Rate_Comm/ReportToCongress2002WEB.txt
government//Post_Rate_Comm/WolakSpeech_usps.txt
government//Media/Federal_agency.txt
government//Media/water_fees.txt
government//Media/Helping_Out.txt
government//Media/balance_scales_of_justice.txt
government//Media/BusinessWire2.txt
government//Media/Legal-aid_chief.txt
government//Media/Unusual_Woodburn.txt
government//Media/Funding_cuts_force.txt
government//Media/Good_guys_reward.txt
government//Media/Anthem_Payout.txt
government//Media/Donald_Hilliker.txt
government//Media/Free_legal_service.txt
government//Media/Owning_a_Piece.txt
government//Media/Targeting_Domestic_Violence.txt
government//Media/highlight_Senior_Day.txt
government//Media/State_funding.txt
government//Media/Few_who_need.txt
government//Media/City_Council_Budget.txt
government//Media/Legal_system_fails_poor.txt
government//Media/Supporting_Legal_Center.txt
government//Media/Lindsays_legacy.txt
government//Media/New_funding_sources.txt
government//Media/Barnes_new_job.txt
government//Media/Providing_Legal_Aid.txt
government//Media/Nonprofit_Buys.txt
government//Media/Legal_Aid_in_Clay_County.txt
government//Media/Domestic_Violence_Ruling.txt
government//Media/Abuse_penalties.txt
government//Media/Law_Award_from_College.txt
government//Media/Law_Schools.txt
government//Media/Raising_the_Bar.txt
government//Media/Justice_for_all.txt
government//Media/agency_expands.txt
government//Media/Helping_Hands.txt
government//Media/Legal_hotline.txt
government//Media/not_accessible_to_disabled.txt
government//Media/Campaign_Pays.txt
government//Media/New_Online_Resources.txt
government//Media/Annual_Fee.txt
government//Media/Oregon_Poor.txt
government//Media/Barnes_pro_bono.txt
government//Media/Poor_Lacking_Legal_Aid.txt
government//Media/Paralegal_Honored.txt
government//Media/Workers_aid_center.txt
government//Media/Philly_Lawyers.txt
government//Media/Too_Crucial_to_Take_Cut.txt
government//Media/Pro_Bono_Services.txt
government//Media/Rumble_in_the_Bronx.txt
government//Media/FortWorthStarTelegram.txt
government//Media/predatory_loans.txt
government//Media/Survey.txt
government//Media/AP_LawSchoolDebts.txt
government//Media/Working_for_Free.txt
government//Media/Eviction_law.txt
government//Media/Law-school_grads.txt
government//Media/FY_04_Budget_Outlook.txt
government//Media/help_rent-to-own_tenants.txt
government//Media/Texas_Lawyer.txt
government//Media/Disaster_center.txt
government//Media/Kiosks_for_court_forms.txt
government//Media/Higher_Registration_Fees.txt
government//Media/Fire_Victims_Sue.txt
government//Media/Funds_Shortage.txt
government//Media/Terrorist_Attack.txt
government//Media/Butler_Co_attorneys.txt
government//Media/BergenCountyRecord.txt
government//Media/families_saved.txt
government//Media/Court_Keeps_Judge_From.txt
government//Media/Volunteers_Step_Up.txt
government//Media/Coup_Reshapes_Legal_Aid.txt
government//Media/IOLTA_INTEREST_RATE.txt
government//Media/Ginny_Kilgore.txt
government//Media/Legal_Aid_looks_to_legislators.txt
government//Media/Poverty_Lawyers.txt
government//Media/Wingates_winds.txt
government//Media/Avoids_Budget_Cut.txt
government//Media/grants_fail_to_come.txt
government//Media/Lockyer_Warns.txt
government//Media/It_Pays_to_Know.txt
government//Media/Self-Help_Website.txt
government//Media/Rental_rules.txt
government//Media/Using_Tech_Tools.txt
government//Media/Assuring_Underprivileged.txt
government//Media/Boone_legal_service.txt
government//Media/Firm_to_the_Poor_Needs_Help.txt
government//Media/Making_a_case.txt
government//Media/Barnes_Volunteers.txt
government//Media/Commercial_Appeal.txt
government//Media/Justice_requests.txt
government//Media/Free_Legal_Assistance.txt
government//Media/Local_Attorneys.txt
government//Media/Texas_Supreme_Court.txt
government//Media/Civil_Matters.txt
government//Media/Low-income_children.txt
government//Media/man_on_national_team.txt
government//Media/BusinessWire.txt
government//Media/Funding_May_Limit.txt
government//Media/The_Columbian.txt
government//Media/Higher_court.txt
government//Media/Service_Agency.txt
government//Media/Marylands_Legal_Aid.txt
government//Media/Bias_on_the_Job.txt
government//Media/Attorney_gives_his_time.txt
government//Media/Library_Lawyers.txt
government//Media/Crains_New_York_Business.txt
government//Media/Hard_to_Get.txt
government//Media/The_State_of_Pro_Bono.txt
government//Media/residents_sue_city.txt
government//Media/Legal_Aid_Society.txt
government//Media/GreensburgDailyNews.txt
government//Media/Major_Changes.txt
government//Media/Program_Lodges.txt
government//Media/Wilmington_lawyer.txt
government//Media/All_May_Have_Justice.txt
government//Media/Domestic_violence_aid.txt
government//Media/Advocate_for_Poor.txt
government//Media/fight_domestic_abuse.txt
government//Media/CommercialAppealMemphis2.txt
government//Media/Weak_economy.txt
government//Media/Lawyer_Web_Survey.txt
government//Media/Valley_Needing_Legal_Services.txt
government//Media/Barr_sharpening_ax.txt
government//Media/Legal_Aid_attorney.txt
government//Media/The_Bend_Bulletin.txt
government//Media/Legal_services_for_poor.txt
government//Media/Farm_workers.txt
government//Media/Entities_Merge.txt
government//Media/less_legal_aid.txt
government//Media/Understanding.txt
government//Media/Do-it-yourself_divorce.txt
government//Media/Politician_Practices.txt
government//Media/defend_yourself.txt
government//Media/Towson_Attorney.txt
government//Media/Pro-bono_road_show.txt
government//Media/A_Perk_of_Age.txt
government//Media/A_helping_hand.txt
government//Media/pro_bono_efforts.txt
government//Media/5_Legal_Groups.txt
government//Media/Greedy_Generous.txt
government//Media/Retirement_Has_Its_Appeal.txt
government//Media/RoanokeTimes.txt
government//Media/NJ_Legal_Services.txt
government//Media/Bridging_legal_aid_gap.txt
government//Media/Legal_Aid_campaign.txt
government//Media/Aid_Gets_7_Million.txt
```
This command is use to find all the regular files in the government/ directory. It is useful to show only the regular files in the given location. 
Reference:https://man7.org/linux/man-pages/man1/find.1.html
```
hogan@Hogans-MacBook-Air technical % find government/ -type d
government/
government//About_LSC
government//Env_Prot_Agen
government//Alcohol_Problems
government//Gen_Account_Office
government//Post_Rate_Comm
government//Media
```
This command is use to find all directories within the government/ directory. It is useful when users only look for directories.
Reference:https://man7.org/linux/man-pages/man1/find.1.html

```
hogan@Hogans-MacBook-Air technical % find 911report/ -name "*.txt"
911report//chapter-13.4.txt
911report//chapter-13.5.txt
911report//chapter-13.1.txt
911report//chapter-13.2.txt
911report//chapter-13.3.txt
911report//chapter-3.txt
911report//chapter-2.txt
911report//chapter-1.txt
911report//chapter-5.txt
911report//chapter-6.txt
911report//chapter-7.txt
911report//chapter-9.txt
911report//chapter-8.txt
911report//preface.txt
911report//chapter-12.txt
911report//chapter-10.txt
911report//chapter-11.txt
hogan@Hogans-MacBook-Air technical % 

```
This command is use to find all .txt files in the 911report folder. It is useful when users only look for a specific file type.
Reference: https://ucsd-cse15l-f23.github.io/week/week4/#symptoms-and-failure-inducing-inputs

```
hogan@Hogans-MacBook-Air technical % find 911report/ -name "*8*"
911report//chapter-8.txt
hogan@Hogans-MacBook-Air technical % 
```
This command is finding the files with "8" in names within 911report/ directory. It is useful when looking for files with a specific pattern in the filename.

Reference:https://man7.org/linux/man-pages/man1/find.1.html