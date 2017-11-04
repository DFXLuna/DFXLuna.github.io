### Slumlord Simulator: An Isometric Town Management Game

Slumlord Simulator was a project undertaken to gain experience in C# and Unity. It is and will forever be unfinished.


#### Summary
Scripts are stored in the [/Assets/_script/](https://github.com/DFXLuna/Slumlord-Simulator/tree/master/Assets/_script) or [/Assets/_script/_helpers](https://github.com/DFXLuna/Slumlord-Simulator/tree/master/Assets/_script/_helpers)

Most of the business logic is in [HomeManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/HomeManager.cs). Game state is maintained across scenes using [PersistanceManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/PersistanceManager.cs). The Slumscript language was implemented so that non-programmers could write narratives in a format that could be directly interpreted by the game. The interpreter is in [NarrativeReader.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/_helpers/NarrativeReader.cs) and the script syntax verifier is in [verify.py](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/verify.py).

#### HomeManager

* Manages buildings spawned on tiles as seen in gifs below.
* Queries [EconomyManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/EconomyManager.cs), [GridManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/GridManager.cs) and [TenantManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/TenantManager.cs) to manage game state in a distributed, object-oriented way.

#### PersistanceManager

* Implements storage to save game state across scenes.
* All objects communicate across the design hierarchy to the [PersistanceManager](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/PersistanceManager.cs) in a loosely coupled way.

#### Slumscript

* Interpreter implemented in [NarrativeReader.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/_helpers/NarrativeReader.cs) which builds narrative objects using the provided .slum file and passes a delegate to call the narrative to the [NarrativeManager.cs](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/NarrativeManager.cs)
* When a narrative's condition to be called is met, the [NarrativeManager](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/NarrativeManager.cs) sets up the storage in the [PersistanceManager](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/PersistanceManager.cs) for the [DialogueManager](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/DialogueManager.cs) to create the necessary scene.
* Game state is accessible in scripts through the [getVariable()](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/Assets/_script/NarrativeManager.cs#L42-L53) method
* The Narrative front end never saw the light of day, but most of the backend is there.
* [Syntax](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/SlumScriptSyntax.md)
* [Example](https://github.com/DFXLuna/Slumlord-Simulator/blob/master/NarrativeFileExample.slum)


#### Some Gifs
<img src="../images/SS1.gif">
<img src="../images/SS2.gif">
