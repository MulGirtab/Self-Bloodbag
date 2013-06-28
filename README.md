Self-Bloodbag
=============

This is just a re-post for <a href="http://opendayz.net/threads/krixes-self-bloodbag-script.9212/">Krixes - Self Bloodbag Script</a>. I am not the creator of this. I simply updated it to 1.7.7.1

Self Bloodbags fully working, plus it fixes the problem with Auto Refuel
--------------------------------------------------------------------
FRESH INSTALL
-------------
Put all these files in the same folder in YOUR MISSION PBO.

<h3>Step 1:</h3>
Open the "fn_selfActions.sqf" file in your Self Bloodbag folder
Look for this around line 51:

    s_player_selfBloodbag = player addaction[("<t color=""#c70000"">" + ("Self Bloodbag") +"</t>"),"YOURFOLDER\player_selfbloodbag.sqf","",5,false,true,"", ""];

Where it says YOURFOLDER change it to where your self bloodbag files is.

<h3>Step 2:</h3>
Open the included compiles.sqf.

On Line 1 change the YOURFOLDER to the location of your file.

<h3>Step 3:</h3>
Open your init.sqf

Look for:

    progressLoadingScreen 1.0;
    
and add this to the line above it:

    call compile preprocessFileLineNumbers "YOURFOLDER\compiles.sqf"; //Compile custom compiles

Make sure it points to the included compiles.sqf



PREEXISTING fn_selfActions.sqf
------------------------------
If you already have a fn_selfActions.sqf in your mission PBO.
<h3>Step 1:</h3>
Look for:

    _canDo = (!r_drag_sqf and !r_player_unconscious and !_onLadder);
    
and add this just after it:

    // ---------------------------------------Krixes Self Bloodbag Start------------------------------------
    _mags = magazines player;
 
    // Krixes Self Bloodbag
    if ("ItemBloodbag" in _mags) then {
        hasBagItem = true;
    } else { hasBagItem = false;};
    if((speed player <= 1) && hasBagItem && _canDo) then {
        if (s_player_selfBloodbag < 0) then {
            s_player_selfBloodbag = player addaction[("<t color=""#c70000"">" + ("Self Bloodbag") +"</t>"),"YOURFOLDER\player_selfbloodbag.sqf","",5,false,true,"", ""];
        };
    } else {
        player removeAction s_player_selfBloodbag;
        s_player_selfBloodbag = -1;
    };
    // ---------------------------------------Krixes Self Bloodbag End------------------------------------

Now in the above code edit YOURFOLDER in this line:

    s_player_selfBloodbag = player addaction[("<t color=""#c70000"">" + ("Self Bloodbag") +"</t>"),"YOURFOLDER\player_selfbloodbag.sqf","",5,false,true,"", ""];
 
<h3>Step 2:</h3>
Open the included compiles.sqf.

On Line 1 change the YOURFOLDER to the location of your file.

<h3>Step 3:</h3>
Open your init.sqf

Look for:

    progressLoadingScreen 1.0;
    
and add this to the line above it:

    call compile preprocessFileLineNumbers "YOURFOLDER\compiles.sqf"; //Compile custom compiles

Make sure it points to the included compiles.sqf
