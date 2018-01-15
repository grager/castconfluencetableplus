## Dynamic Filter

<script>

var totalnb = $("tbody").find("tr").find("td:first").length;
var totaldonenb = $("tbody").find("tr").find("td:first[data-highlight-colour='green']").length;
var totalabandonnednb = $("tbody").find("tr").find("td:first[data-highlight-colour='grey']").length;
var totalspecifiednb = $("tbody").find("tr").find("td:first[data-highlight-colour='blue']").length;
var totalcandidatenb = $("tbody").find("tr").find("td:first[data-highlight-colour='yellow']").length;
var totaliceboxnb = totalnb - totaldonenb - totalabandonnednb - totalspecifiednb - totalcandidatenb;



var liststatus = $("span[data-macro-name=status]");
var keyliststatus = {};
 
$.each(liststatus , function( index, value ) {
	
	//console.log(value+" -> "+index+":"+value.innerHTML);

	var valueHTML = value.innerHTML;
	var currentIndex = keyliststatus[valueHTML];
	
	
	if($(value.parentElement.parentElement.parentElement).hasClass("highlight-green"))
	{
		$(value.parentElement.parentElement.parentElement.parentElement).addClass(value.innerHTML);
		if(currentIndex && (currentIndex>0))
		{
			currentIndex = currentIndex + 1;
		}
		else
		{
			currentIndex = 1;
		}

		keyliststatus[valueHTML] = currentIndex;
	}

});

var valuestream = "<h4><ul style='background-color: #FFF; list-style-type: none; margin: 0; padding: 0; overflow: hidden;'>";

$.each(keyliststatus, function(key, value) {
	
	valuestream += "<li style='float: left;'><a href='#"+key+"' style='color:black; display: block; padding: 10px; text-decoration: none;'>"+key+": "+value+"</a></li>";
	
});

valuestream += "</ul></h4>";

$(".table-wrap").prepend(valuestream);
 
 
$("h4 a").click(function() {
	console.log($(this).attr("href"));

	$("h4 a").css("border-style","none");
	$(this).css("border-style","dotted");

	$("tbody").find("tr").hide();
	$("tbody").find("tr."+$(this).attr("href").substring(1)).show();
 
});

$(".table-wrap").prepend("<h3>Hereafter the list of the rules that could be filtered using the following Tabbar:<br/><br/><ul style='background-color: #FFF; list-style-type: none; margin: 0; padding: 0; overflow: hidden;'><li style='float: left;'><a href='#total' style='border-style: solid; color:black; display: block; padding: 10px; text-decoration: none;'>Total: "+
totalnb+
"</a></li><li style='float: left;'><a href='#icebox' style='color: #AAA; display: block; padding: 10px; text-decoration: none;'>Icebox: "+
totaliceboxnb+
"</a></li><li style='float: left;'><a href='#abandonned' style='color: #CCC; background-color: #ddd; display: block; padding: 10px; text-decoration: none;'>Abandonned: "+
totalabandonnednb+
"</a></li><li style='float: left;'><a href='#candidate' style='color: #ffd351; background-color: #FFD; display: block; padding: 10px; text-decoration: none;'>Candidate: "+
totalcandidatenb+
"</a></li><li style='float: left;'><a href='#specified' style='color: #4A6785; background-color: #E0F0FF; display: block; padding: 10px; text-decoration: none;'>Specified: "+
totalspecifiednb+
"</a></li><li style='float: left; '><a href='#done' style='color: #14892C;  background-color: #ddfade;  display: block; padding: 10px; text-decoration: none;'>Done: "+
totaldonenb+
"</a></li></ul></h3>");

$("h3 a").click(function() { 
	
	//console.log($(this).attr("href"));
	
	$("h4 a").css("border-style","none");
	$("tbody").find("tr").show();

	
	$("h3 a").css("border-style","none");
	$(this).css("border-style","solid");
	
	if($(this).attr("href") == "#done")
	{
		$("tbody").find("tr").find("td").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='green']").show();
	}
	else if($(this).attr("href") == "#abandonned")
	{
		$("tbody").find("tr").find("td").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='grey']").show();
	}
	else if($(this).attr("href") == "#candidate")
	{
		$("tbody").find("tr").find("td").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='yellow']").show();
	}
	else if($(this).attr("href") == "#specified")
	{
		$("tbody").find("tr").find("td").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='blue']").show();
	}
	else if($(this).attr("href") == "#icebox")
	{
		$("tbody").find("tr").find("td").show();
		$("tbody").find("tr").find("td[data-highlight-colour='blue']").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='grey']").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='yellow']").hide();
		$("tbody").find("tr").find("td[data-highlight-colour='green']").hide();
	}
	else if($(this).attr("href") == "#total")
	{
		$("tbody").find("tr").find("td").show();
	}
	
	});
 
    // --- CISQ covergae ---
 
	var cisqstream = '{"ASCMM-MNT-01":"Control Flow Transfer Control Element outside Switch Block","ASCMM-MNT-02":"Class Element Excessive Inheritance of Class Elements with Concrete Implementation","ASCMM-MNT-03":"Storable and Member Data Element Initialization with Hard-Coded Literals","ASCMM-MNT-04":"Callable and Method Control Element Number of Outward Calls","ASCMM-MNT-05":"Loop Value Update within the Loop","ASCMM-MNT-06":"Commented Code Element Excessive Volume","ASCMM-MNT-07":"Inter-Module Dependency Cycles","ASCMM-MNT-08":"Source Element Excessive Size","ASCMM-MNT-09":"Horizontal Layer Excessive Number","ASCMM-MNT-10":"Named Callable and Method Control Element Multi-Layer Span","ASCMM-MNT-11":"Callable and Method Control Element Excessive Cyclomatic Complexity Value","ASCMM-MNT-12":"Named Callable and Method Control Element with Layer-skipping Call","ASCMM-MNT-13":"Callable and Method Control Element Excessive Number of Parameters","ASCMM-MNT-14":"Callable and Method Control Element Excessive Number of Control Elements involving Data Element from Data Manager or File Resource","ASCMM-MNT-15":"Public Member Element","ASCMM-MNT-16":"Method Control Element Usage of Member Element from other Class Element","ASCMM-MNT-17":"Class Element Excessive Inheritance Level","ASCMM-MNT-18":"Class Element Excessive Number of Children","ASCMM-MNT-19":"Named Callable and Method Control Element Excessive Similarity","ASCMM-MNT-20":"Unreachable Named Callable or Method Control Element","ASCPEM-PRF-01":"Static Block Element containing Class Instance Creation Control Element","ASCPEM-PRF-02":"Immutable Storable and Member Data Element Creation","ASCPEM-PRF-03":"Static Member Data Element outside of a Singleton Class Element","ASCPEM-PRF-04":"Data Resource Read and Write Access Excessive Complexity","ASCPEM-PRF-05":"Data Resource Read Access Unsupported by Index Element","ASCPEM-PRF-06":"Large Data Resource ColumnSet Excessive Number of Index Elements","ASCPEM-PRF-07":"Large Data Resource ColumnSet with Index Element of  Excessive Size","ASCPEM-PRF-08":"Control Elements Requiring Significant Resource Element within Control Flow Loop Block","ASCPEM-PRF-09":"Non-Stored SQL Callable Control Element with Excessive Number of Data Resource Access","ASCPEM-PRF-10":"Non-SQL Named Callable and Method Control Element with Excessive Number of Data Resource Access","ASCPEM-PRF-11":"Data Access Control Element from Outside Designated Data Manager Component","ASCPEM-PRF-12":"Storable and Member Data Element Excessive Number of Aggregated Storable and Member Data Elements","ASCPEM-PRF-13":"Data Resource Access not using Connection Pooling capability","ASCPEM-PRF-14":"Storable and Member Data Element Memory Allocation Missing De-Allocation Control Element","ASCPEM-PRF-15":"Storable and Member Data Element Reference Missing De-Referencing Control Element","ASCRM-CWE-120":"Buffer Copy without Checking Size of Input","ASCRM-CWE-252-data":"Unchecked Return Parameter Value of named Callable and Method Control Element with Read, Write, and Manage Access to Data Resource","ASCRM-CWE-252-resource":"Unchecked Return Parameter Value of named Callable and Method Control Element with Read, Write, and Manage Access to Platform Resource","ASCRM-CWE-396":"Declaration of Catch for Generic Exception","ASCRM-CWE-397":"Declaration of Throws for Generic Exception","ASCRM-CWE-456":"Storable and Member Data Element Missing Initialization","ASCRM-CWE-674":"Uncontrolled Recursion","ASCRM-CWE-704":"Incorrect Type Conversion or Cast","ASCRM-CWE-772":"Missing Release of Resource after Effective Lifetime","ASCRM-CWE-788":"Memory Location Access After End of Buffer","ASCRM-RLB-01":"Empty Exception Block","ASCRM-RLB-02":"Serializable  Storable Data Element without Serialization Control Element","ASCRM-RLB-03":"Serializable Storable Data Element with non-Serializable Item Elements","ASCRM-RLB-04":"Persistant  Storable Data Element without Proper Comparison Control Element","ASCRM-RLB-05":"Runtime Resource Management Control Element in a Component Built to Run on Application Servers","ASCRM-RLB-06":"Storable or Member Data Element containing Pointer Item Element without Proper Copy Control Element","ASCRM-RLB-07":"Class Instance Self Destruction Control Element","ASCRM-RLB-08":"Named Callable and Method Control Elements with Variadic Parameter Element","ASCRM-RLB-09":"Float Type Storable and Member Data Element Comparison with Equality Operator","ASCRM-RLB-10":"Data Access Control Element from Outside Designated Data Manager Component","ASCRM-RLB-11":"Named Callable and Method Control Element in Multi-Thread Context with non-Final Static Storable or Member Element","ASCRM-RLB-12":"Singleton Class Instance Creation without Proper Lock Element Management","ASCRM-RLB-13":"Inter-Module Dependency Cycles","ASCRM-RLB-14":"Parent Class Element with References to Child Class Element","ASCRM-RLB-15":"Class Element with Virtual Method Element without Virtual Destructor","ASCRM-RLB-16":"Parent Class Element without Virtual Destructor Method Element","ASCRM-RLB-17":"Child Class Element without Virtual Destructor unlike its Parent Class Element","ASCRM-RLB-18":"Storable and Member Data Element Initialization with Hard-Coded Network Resource Configuration Data","ASCRM-RLB-19":"Synchronous Call Time-Out Absence","ASCSM-CWE-022":"Path Traversal Improper Input Neutralization","ASCSM-CWE-078":"OS Command Injection Improper Input Neutralization","ASCSM-CWE-079":"Cross-site Scripting Improper Input Neutralization","ASCSM-CWE-089":"SQL Injection Improper Input Neutralization","ASCSM-CWE-99":"Name or Reference Resolution Improper Input Neutralization","ASCSM-CWE-120":"Buffer Copy without Checking Size of Input","ASCSM-CWE-129":"Array Index Improper Input Neutralization","ASCSM-CWE-134":"Format String Improper Input Neutralization","ASCSM-CWE-252-resource":"Unchecked Return Parameter Value of named Callable and Method Control Element with Read, Write, and Manage Access to Platform Resource","ASCSM-CWE-327":"Broken or Risky Cryptographic Algorithm Usage","ASCSM-CWE-396":"Declaration of Catch for Generic Exception","ASCSM-CWE-397":"Declaration of Throws for Generic Exception","ASCSM-CWE-434":"File Upload Improper Input Neutralization","ASCSM-CWE-456":"Storable and Member Data Element Missing Initialization","ASCSM-CWE-606":"Unchecked Input for Loop Condition","ASCSM-CWE-667":"Shared Resource Improper Locking","ASCSM-CWE-672":"Expired or Released Resource Usage","ASCSM-CWE-681":"Numeric Types Incorrect Conversion","ASCSM-CWE-772":"Missing Release of Resource after Effective Lifetime","ASCSM-CWE-789":"Uncontrolled Memory Allocation","ASCSM-CWE-798":"Hard-Coded Credentials Usage for Remote Authentication","ASCSM-CWE-835":"Loop with Unreachable Exit Condition (Infinite Loop)"}';
 
var alltrs = $('tbody').find('tr');
var alldonetds = [];
var allcandtds = [];
var allspectds = [];

var allCISQItemsDone = [];
var allCISQItemsCand = [];
var allCISQItemsSpec = [];


var cisqstreamArray = [];

var columnIndex = 7;

$.each(alltrs, function(index, value) { alldonetds.push($(value).find("td[data-highlight-colour='green']")[columnIndex ]) });
$.each(alltrs, function(index, value) { allcandtds.push($(value).find("td[data-highlight-colour='yellow']")[columnIndex ]) });
$.each(alltrs, function(index, value) { allspectds.push($(value).find("td[data-highlight-colour='blue']")[columnIndex ]) });
 

$.each(alldonetds, function(index, value) { 

	var str = $(value).text().trim().split(",");
	for(i=0; i<str.length; i++)
	{
		allCISQItemsDone.push(str[i]);
	}
});

$.each(allcandtds, function(index, value) { 

	var str = $(value).text().trim().split(",");
	for(i=0; i<str.length; i++)
	{
		allCISQItemsCand.push(str[i]);
	}
	
});

$.each(allspectds, function(index, value) {

	var str = $(value).text().trim().split(",");
	for(i=0; i<str.length; i++)
	{
		allCISQItemsSpec.push(str[i]);
	}

});

 
var cisqitemdonelist = {};
var cisqitemcandlist = {};
var cisqitemspeclist = {};
 
	JSON.parse(cisqstream,(key,value) => { 
 
	cisqstreamArray[key] = value;
	var cisqrulecount = 0;
 
	for (i = 0; i < allCISQItemsDone.length; i++) { 
 
		if(allCISQItemsDone[i] == key)
		{
    		cisqrulecount += 1;
		}
	}
 
	cisqitemdonelist[key] = cisqrulecount;
 
	cisqrulecount = 0;
 
	for (i = 0; i < allCISQItemsCand.length; i++) { 
 
		if(allCISQItemsCand[i] == key)
		{
    		cisqrulecount += 1;
		}
	}
 
	cisqitemcandlist[key] = cisqrulecount;
 
	cisqrulecount = 0;
 
	for (i = 0; i < allCISQItemsSpec.length; i++) { 
 
		if(allCISQItemsSpec[i] == key)
		{
    		cisqrulecount += 1;
		}
	}
 
	cisqitemspeclist[key] = cisqrulecount;
 
});
 
var cisqoutput = "<textarea id='cisqoutput' cols=100 rows=10>";
$.each(cisqitemdonelist, function(index, value) {  if(index.trim() !="") { cisqoutput += ""+index+"\t"+cisqstreamArray[index]+"\t"+value+"\t"+cisqitemspeclist[index]+"\t"+cisqitemcandlist[index]+"\n" }} ); cisqoutput += "</textarea>";
$(".table-wrap").prepend("<h3>CISQ Coverage Output ready for Excel (just copy/paste the textarea)</h3>"+cisqoutput);
 
</script>
