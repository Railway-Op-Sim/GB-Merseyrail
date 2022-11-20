# Merseyrail

The Merseyrail network is primarily for commuters/shoppers heading into and out of Liverpool. It consists of 2 lines - the Northern line from Southport, Ormskirk and Kirkby to Liverpool and Hunts Cross, and the Wirral line from New Brighton, West Kirby, Chester and Ellesmere Port to Liverpool.

The area is mostly controlled by one signalling centre at Sandhills. There are 2 workstations here - the Northern Line workstation controlling Southport, Ormskirk and Kirkby to Liverpool Central (Brunswick - Hunts Cross in real life is controlled by Hunts Cross PSB), and the Wirral Line workstation controlling New Brighton, West Kirby, and Bromborough - Liverpool Loop and Neston - Bidston (Chester/Ellesmere Port - Bromborough in real life is controlled by Chester, Hooton and Ellesmere Port PSB's).

At some stations I have simplified the layout to what is needed for the purpose of this simulation. These are outlined as follows:
-- Chester: I have only included the electrified tracks, in reality the layout is much more complex
-- Hunts Cross: I have only included the electrified tracks, these tracks do cross the unelectrified lines from Liverpool to Manchester via Warrington
-- Kirkby: There is another single track (unelectrified) on the otherside of the buffer stops, with trains to Manchester via Wigan. There is currently a station under construction between Kirkby and Rainford (the next station towards Wigan), which once built will be the new interchange point for Northern and Merseyrail services
-- Ormskirk: Similar to Kirkby, there is another single track (unelectrified) on the otherside of the buffer stops, making a single long platform, with trains to Preston
-- Southport: In addition to the simulated platforms, there are another few (unelectrified) platforms with Northern trains to Manchester via Wigan

## Simulation

I have included a representation timetable of the services operated on the network. These includes all the services and frequencies of the trains that actually operate, but not neccessarily to the same timings or with the same start/finish to the service. The timetable lasts about 6 hours during the morning, with a service start, finish and a few hours of standard operation.

Below is a summary of the services that operate, with a more detailed summary and some operation tips for each service after. All Wirral line and Northern line headcodes have been linked, so you should find this useful when merging trains at Hamilton Square and in the Kirkdale area.
-- New Brighton - Liverpool Loop (4tph)
-- West Kirby - Liverpool Loop (4tph)
-- Wrexham - Bidston (1tph)
-- Chester - Liverpool Loop (4tph)
-- Ellesmere Port - Liverpool Loop (2tph)
-- Kirkby - Liverpool Central (4tph)
-- Ormskirk - Liverpool Central (4tph)
-- Southport - Hunts Cross (4tph)

The included session file contains preset automatic routes that will be needed throughout the simulation. There are some locations you can use automatic routes once trains have left the depot, but you may need to break these later on to let trains back in. Only put these routes in if you aren't likely to forget later.

Do not be afraid to make ECS (5XXX headcodes) trains wait, they usually have lots of slack and may well have schedule conflicts with other services.

### New Brighton

These trains run from New Brighton - New Brighton via the Liverpool Loop using the 2NXX headcode. There is nothing complicated about them, though you may need to hold trains outside New Brighton while the outbound train leaves.

### West Kirby

These trains run from West Kirby - West Kirby via the Liverpool Loop using the 2WXX headcode. There is a high number of level crossing between Bidston and West Kirby, so try not to set routes too early. Trains should pass at Hoylake, so you will probably keep that crossing open for both trains. There is 1 train at start of service, and 1 train at the end, that need to be shunted to/from the sidings. The schedule has these trains shunt through Hoylake station (which requires a "red route" to get to), but you can reverse them in the signal block before the crossing by using signaller control to reverse them (and skipping the Hoylake stop).

### Wrexham - Bidston

These trains run from Wrexham - Bidston once every hour using the 2FXX/2JXX headcodes. They tend to arrive on the simulation very early, so you are likely to need to make them wait for the West Kirby trains to pass before signalling them into the platform. They should use the lower platform at Bidston, but if you are experiencing disruption with the West Kirby trains feel free to reverse them outside Bidston station and use platforms one directionally.

### Ellesmere Port

These trains only run twice per hour, from Ellesmere Port - Ellesmere Port via the Liverpool Loop using the 2YXX headcode. Towards the end of service, these trains return to random locations. The train that stables at Rock Ferry should do so in platforms 3 or 4 (the bay platforms). The train that runs passenger from Ellesmere Port to Hooton should terminate and stable in the bay platform there (platform 1). The train that runs ECS to Hooton should go through platform 0 and into the station sidings.

### Chester

These trains run from Chester - Chester via the Liverpool Loop using the 2CXX headcode. These trains have only 2 minutes dwell time at Chester before returning, so you should do your best to avoid delaying these trains. You should prioritse these trains over any other service at merges and flat crossings if such conflict were to happen since other routes have much more dwell time. At the end of service, there are multiple locations trains run to. The train that stables at Rock Ferry should do so in platforms 3 or 4 (the bay platforms). The train that terminates at James Street then runs into the siding should use platform 2 at James Street (the middle one). The train that terminates at Spital and then runs into Port Sunlight siding will need care to ensure it doesn't continue towards Rock Fery. The 3 trains that run ECS from Chester to Hooton should ensure they arrive at Hooton in the correct order to avoid blocking paths to their correct stabling points.

### Kirkby

These trains between Kirkby and Liverpool Central using the 2KXX headcode. In reality these trains run into Liverpool on the 2GXX headcode, and out again with 2KXX, but for simplicity I am using odd XX's into Liverpool and even's back to Kirkby. They turn round in platform 1 (the upper one) at Liverpool Central, but if there are any delays you may choose to turn them around in platform 2 or use the reversing siding. They can return to either end of Kirkdale TMD, but the Northern end is the more appropriate end to use. The distance between Kirkby and Fazakerley is fairly long, so don't set routes out of Kirkby until the train is nearly ready to leave to avoid unneccessary crossing wait times.

### Ormskirk

These trains run between Ormskirk and Liverpool Central using the 2OXX headcode. In reality these trains run into Liverpool on the 2GXX headcode, and out again with 2OXX, but for simplicity I am using odd XX's into Liverpool and even's back to Ormskirk. They arrive in platform 1 at Liverpool Central, drive into the reversing siding and back out for departure from platform 2. If there is a service irregularity, you may wish to turn these trains round in the platforms at Liverpool Central. They can return to either end of Kirkdale TMD, but the Northern end is the more appropriate end to use.

### Southport

These trains run between Southport and Hunts Cross via Liverpool Central using the 2UXX/2SXX headcodes. 4 trains start/finish in the Birkdale sidings, with the rest using Southport platforms. Once service has started, you will need to use at least 2 platforms at Southport to turn trains round in. It is recommended to use platforms 2 and 3 (the upper pair) so that you do not need to think about which platforms trains need to go into if they are returning to Birkdale sidings. At Hunts Cross, you should primarily use platform 3 (the upper one), using only platform 2 in severe disruption due to this being a through running line on the Liverpool - Manchester line. Generally, you should treat the line as single track from Liverpool South Parkway. There is a high level of level crossings between Southport and Waterloo, so try not to set routes too early.

### Rescue Locomotives

Rescue Locos with the headcode 0Z00 have been placed in various sidings accross the network. These can be used to rescue failed trains. Once a train has been rescued you should drag them straight to either Birkenhead North or Kirkdale TMD's since the locomotives do not have anywhere near enough power to pull the whole train for passenger service.

## Development

This route is open source and you can help contribute on [GitHub](https://github.com/Railway-Op-Sim/GB-Merseyrail). Please make an issue (or even a pull request) if you find bugs or have a suggestion to make the route better!

If you would like to do something for this route, but are at a loss for what to do, either check the issues tab on GitHub or here are some ideas: create a full day representation timetable, create the real timetable, create any fictional timetable you can think of.

If you have any problems while contributing for this route, you can join the [discord server](https://discord.gg/FmE8dxN) and ping mathstrains19#2057 or ask anyone around for help in the relevant chat channels. Don't forget to check the manual before asking questions, since they may already be answered there!
