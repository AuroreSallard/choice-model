# Updated mode choice model for Île-de-France

cleaning of data
- surveys/egt_2010/Clean EGT.ipynb
- surveys/egt_2010/Spatialize EGT.ipynb
- surveys/egt_2010/Availabilities.ipynb

(calibration of transit routing model)
- transit/Prepare reference.ipynb (prepares data from cleaned survey)
- transit/Calibration.ipynb (runs for multiple days)
- transit/Calibration progress.ipynb (to run to see the progress)


# Routing server
    Clone https://github.com/eqasim-org/eqasim-java/tree/feat/freeflow-calibration
    Branch develop
    Run server using org.eqasim.server.RunServer
    with arguments:
        --config-path idf_1pm_config.xml
        --port 8054

Routing of transit alternatives
- transit/Perform routing.ipynb to obtain public transport routes for all trips
  think about adjusting routing_endpoint in the notebook

(calibration of road routing model for freeflow travel tiles)
- road/freeflow/Prepare * reference.ipynb prepares either all trips at 4am of EGT or all trips routed via TomTom at 4am to obtain freeflow travel times vs. speed limits
- road/freeflow/Calibration.ipynb turn multiple days
- road/freeflow/Calibration progress.ipynb

(calibration of road routing model for congested travel times)
- road/congestion/Calculate congestion.ipynb


Routing of road alternatives
- road/congestion/Perform routing.ipynb
  adjust routing_endpoint correctly

Now necessary to run routing server with branch feat/freeflow-calibration


# Prepare information for parking

bd-topo in resources/network
IRIS data in resources/iris
RP Logement 2019 in resources/housing

- Clean network takes the raod network from BD-TOPO and extracts road distance per IRIS
- Clean ownership takes the INSEE RP Logement data and extracts registered vehicles per IRIS
- Prepare parking pressure calculates vehicles / road distance

# Choice model

- choice_model/Prepare model.ipynb
- choice_model/Estimate model.ipynb

- TODO: Merge evrything in the eqasim-java server routing part (freespeed settings with crossing penalties)