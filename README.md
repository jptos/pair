# pair
(c) 2015 Sean Patrick Burke

Non-IFW PAIR data tabs. Includes basic application information. Not as complete as published application data.

pf.pl - A perl script for pulling PAIR data

usage: pf.pl [\<Application Number\>] [CSV]

If no arguments are provided, the script will crawl ReedTech's public data. As of September 2015, there are approximately 5.2 million records. If you don't feel like generating your own db, feel free to download the quarterly dataset posted here:.

You will need the following components to run this script: DBI:SQLite 


This is a script designed to populate a SQLITE db (or optionally, a collection of CSV tables) with PAIR metadata. Data is arranged in tables according to the PTO's PAIR layout information. The code is designed to politely pull data using gsutil and afterwards arrange it in the following tables:

Attorney and Agent Information:

AAP (Attorney Names, Regs. and Phones)
    ---> Name
    ---> Reg (Registration Num.)
    ---> Phone

ATAP (Attorney Applications)
    ---> Reg (Registration number)
    ---> Appl (Application number)
    
APP
    ---> AID (Application number)
    ---> Name (firm name)
    ---> Addr (firm address)
    ---> CustNo (firm customer number)
    
Application Data:

ADATA
    ---> AID (Application Number. See http://www.uspto.gov/web/offices/ac/ido/oeip/taf/filingyr.htm for details)
    ---> FDATE (Filing or 371(c) date; American style MM-DD-YYYY)
    ---> TYPE (Application Type: DESIGN, PLANT, REEXAM, REISSUE, UTILITY)
    ---> EXNM (Examiner name: Last, First)
    ---> GAU  (Group art unit)
    ---> CNNO (Confirmation number)
    ---> ATNO (Attorney docket number)
    ---> CSC  (USPC Class/Subclass)
    ---> FNI ("First Name Inventor" e.g. Oswald Cobblepot, Gotham, NJ)
    ---> CustNo (firm customer number)
    ---> LOC (Should always be "ELECTRONIC")
    ---> LOCDATE (Location date. Should be same as filing).
    ---> EPNO   (Earliest publication number.)
    ---> EPDATE (Earliest publication date.)
    ---> PNUM  (Patent number) 
    ---> ISDATE (Patent issue date)
    ---> TITLE (Patent title)

STS (Status)
    ---> AID (App. number)
    ---> Status (Possible Status text value: “Docketed New Case - Ready for Examination”, “Application Dispatched from Preexam, Not Yet Docketed”, “Publications -- Issue Fee Payment Verified”, “Patented Case”, “Reexamination Certificate Issued”)
    ---> STDATE (Status Date: MM-DD-YYYY)

CONT (Continuity Data)
    ---> AID (App. number)
    ---> DESC (Description) 
    ---> PRNTNUM (Parent Number)
    ---> PFDate (Parent filing date)
    ---> PSTAT (Parent status)
    ---> PATNUM (Patent Number)

FP (Foreign Priority)
    ---> AID (App. number)
    ---> CT (Country)
    ---> PRIORITY (Priority number)
    ---> PDATE (Priority date MM-DD-YYYY)

TX (Transaction history)
    ---> AID (App. number)
    ---> TDATE (Transaction date)
    ---> TXN (Transaction Description)


