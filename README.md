# GlitchHunterCoder 
Hello i am `GlitchHunterCoder` and i code using JS to code for [![bloxd.io](https://img.shields.io/badge/bloxd.io-2E80EE?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAQKADAAQAAAABAAAAQAAAAABGUUKwAAABJUlEQVR4Ae2bIQ7CQBREt6SHwECCRBEsjgRFAhoFAoFBI5oQHCfAICrqCJYDICsRFRjuAgl+ZwWG5E3t7G468990VbPJoPMO4KcF9v617gBMADwBVwAOQDABJgCegCsAB8AfQVfAFYAn4ArAAfAt4Aq4AvAEXAE4ACFPBVDMxqklf60fb3f5fq6AjAcgmgDAkKVFEyDjAYh4AvLUPT86lJKDzeIh9VX/JPWUWD23csn5MpR6EdZSxxPgACQfANEEAIYsLZoAGQ9AzLu99k8262Yp9++nc6mnxPqqzw+hkUek/LkCMj6AaAIAQ5YWTYCMByDiCche5c7/CwBIj1rEV8ABRNmACCYAMuioTRMQjQYimADIoKM2TUA0GohgAiCDjtrEE/ABsvEXml+cvPwAAAAASUVORK5CYII=&style=for-the-badge)](https://bloxd.io)

<div align="center">
<!--
[![CI](https://github.com/fastify/fastify/workflows/ci/badge.svg)](https://github.com/fastify/fastify/actions/workflows/ci.yml)
[![Package Manager CI](https://github.com/fastify/fastify/workflows/package-manager-ci/badge.svg)](https://github.com/fastify/fastify/actions/workflows/package-manager-ci.yml)
[![Web SIte](https://github.com/fastify/fastify/workflows/website/badge.svg)](https://github.com/fastify/fastify/actions/workflows/website.yml)
[![Known Vulnerabilities](https://snyk.io/test/github/fastify/fastify/badge.svg)](https://snyk.io/test/github/fastify/fastify)
[![Coverage Status](https://coveralls.io/repos/github/fastify/fastify/badge.svg?branch=main)](https://coveralls.io/github/fastify/fastify?branch=main)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://standardjs.com/)
-->
</div>

## Socials
My Socials Are: 
- [Discord Profile](https://discord.com/users/1054017238606286928)
- [Discord Server for Advanced Coders](https://discord.gg/nTTktDKVZx)
- [Fandom Profile](https://bloxd-io.fandom.com/wiki/User:GlitchHunterCode)
## Skills

<p align="center"><a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com?font=Fira+Code&duration=1000&pause=1000&width=180&color=808080&lines=Bloxd+Io+Coder" alt="Typing SVG" /></a></p>

<p align="center">
  <img width="104.25" height="104.25" alt="image" src="https://github.com/user-attachments/assets/d833ae7a-2b3c-4bfc-961b-3f1a0287f0a3" />
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=discord,github,js,windows&perline=2" />
  </a> 
</p>

<details>
  <summary>Bloxd Runtime Graph</summary>

```mermaid
---
title: Interruption Model
---
stateDiagram-v2
  classDef Halt fill:#f00,color:white,font-weight:bold,stroke-width:2px,stroke:black
  classDef WorldCodeStyle fill:#000,color:purple,font-weight:bold,stroke-width:6px,stroke:purple
  classDef CodeBlockStyle fill:#000,color:white,font-weight:bold,stroke-width:6px,stroke:#gray
  classDef BloxdLoadStyle fill:#008,color:white,font-weight:bold,stroke-width:6px,stroke:#004, text-shadow: 2px 2px blue
  classDef ErrorStyle fill:#800,color:white,font-weight:bold,stroke-width:6px,stroke:#400, text-shadow: 2px 2px red
  classDef FatalErrorStyle fill:#f00,color:black,font-weight:bold,stroke-width:6px,stroke:#000, text-shadow: 2px 2px red
  classDef EnvStyle fill:black,color:gold,font-weight:bold,stroke-width:6px,stroke:gold, text-shadow: 2px 2px black

  class WorldCode WorldCodeStyle
  class CodeBlock CodeBlockStyle
  class Activate, Update, Start, End BloxdLoadStyle
  class RateLimit, Interruption ErrorStyle
  class DontRun, StopCode, NoCall FatalErrorStyle
  class Env EnvStyle

  Env: Environment
  Activate: Activation
  [*] --> Activate: onLobbyStart
  Update --> [*]: onLobbyEnd
  Env --> Update
  Update --> Env

  state Env {
    RateLimit --> WorldCode

    state Activate {
      if_WC_A: if WorldCode Changed
      if_CB_A: if CodeBlock Pressed
      [*] --> if_WC_A
      if_WC_A --> RateLimit: True
      if_WC_A --> if_CB_A: False
      if_CB_A --> CodeBlock: True
      if_CB_A --> NoCall: False
    }

    state CodeBlock {
      myId --> Step_CB
      thisPos --> Step_CB
      Step_CB: Step Execution
      [*] --> Step_CB
      Step_CB --> [*]
    }
    
    state WorldCode {
      [*] --> Init: First Run of code
      Init --> Callbacks?: Gather Function Definitions of Callbacks
      Callbacks? --> Callback: Begin Callback Loop
      Callback --> Called?: Check Call List
      Called? --> Callback: Cycles every 50ms, regardless of callbacks
      
      state Init {
        Step_I: Step Execution
        [*] --> Step_I
        Step_I --> [*]
      }
      
      state Callback {
        Step_C: Step Execution
        [*] --> Step_C
        Step_C --> [*]
      }
    }
    state Interruption {
      [*] --> IU
      IU: IU % 5000 == 0
      IU --> [*]: False
      IU --> TU: True
      TU: TU > TU_limit
      TU --> StopCode: True
      state "Error: Interrupted" as StopCode
      TU --> [*]: False
      [*]
    }
    
    state RateLimit {
      DontRun: "Wait X Seconds Before Running Code"
      [*] --> RT
      RT: TU > TU_limit
      RT --> DontRun: True
      RT --> [*]
    }

    CodeBlock --> Interruption
    WorldCode --> Interruption
    Interruption --> [*]
  }
  state Update {
    [*] --> UpdateData
    UpdateData --> [*]
  }
```

</details>

<details>
  <summary>Voxel Simulator</summary>

```stl
solid merged
facet
outer loop
vertex 0 0 0
vertex 50 0 0
vertex 0 50 0
endloop
endfacet
facet
outer loop
vertex 50 0 0
vertex 50 50 0
vertex 0 50 0
endloop
endfacet
facet
outer loop
vertex 0 0 10
vertex 0 50 10
vertex 50 0 10
endloop
endfacet
facet
outer loop
vertex 50 0 10
vertex 0 50 10
vertex 50 50 10
endloop
endfacet
facet
outer loop
vertex 0 0 0
vertex 0 0 10
vertex 50 0 0
endloop
endfacet
facet
outer loop
vertex 50 0 0
vertex 0 0 10
vertex 50 0 10
endloop
endfacet
facet
outer loop
vertex 0 50 0
vertex 50 50 0
vertex 0 50 10
endloop
endfacet
facet
outer loop
vertex 50 50 0
vertex 50 50 10
vertex 0 50 10
endloop
endfacet
facet
outer loop
vertex 0 0 0
vertex 0 50 0
vertex 0 0 10
endloop
endfacet
facet
outer loop
vertex 0 50 0
vertex 0 50 10
vertex 0 0 10
endloop
endfacet
facet
outer loop
vertex 50 0 0
vertex 50 0 10
vertex 50 50 0
endloop
endfacet
facet
outer loop
vertex 50 50 0
vertex 50 0 10
vertex 50 50 10
endloop
endfacet
facet
outer loop
vertex 20 20 10
vertex 30 20 10
vertex 20 30 10
endloop
endfacet
facet
outer loop
vertex 30 20 10
vertex 30 30 10
vertex 20 30 10
endloop
endfacet
facet
outer loop
vertex 20 20 30
vertex 20 30 30
vertex 30 20 30
endloop
endfacet
facet
outer loop
vertex 30 20 30
vertex 20 30 30
vertex 30 30 30
endloop
endfacet
facet
outer loop
vertex 20 20 10
vertex 20 20 30
vertex 30 20 10
endloop
endfacet
facet
outer loop
vertex 30 20 10
vertex 20 20 30
vertex 30 20 30
endloop
endfacet
facet
outer loop
vertex 20 30 10
vertex 30 30 10
vertex 20 30 30
endloop
endfacet
facet
outer loop
vertex 30 30 10
vertex 30 30 30
vertex 20 30 30
endloop
endfacet
facet
outer loop
vertex 20 20 10
vertex 20 30 10
vertex 20 20 30
endloop
endfacet
facet
outer loop
vertex 20 30 10
vertex 20 30 30
vertex 20 20 30
endloop
endfacet
facet
outer loop
vertex 30 20 10
vertex 30 20 30
vertex 30 30 10
endloop
endfacet
facet
outer loop
vertex 30 30 10
vertex 30 20 30
vertex 30 30 30
endloop
endfacet
facet
outer loop
vertex 0 0 30
vertex 50 0 30
vertex 0 50 30
endloop
endfacet
facet
outer loop
vertex 50 0 30
vertex 50 50 30
vertex 0 50 30
endloop
endfacet
facet
outer loop
vertex 0 0 40
vertex 0 50 40
vertex 50 0 40
endloop
endfacet
facet
outer loop
vertex 50 0 40
vertex 0 50 40
vertex 50 50 40
endloop
endfacet
facet
outer loop
vertex 0 0 30
vertex 0 0 40
vertex 50 0 30
endloop
endfacet
facet
outer loop
vertex 50 0 30
vertex 0 0 40
vertex 50 0 40
endloop
endfacet
facet
outer loop
vertex 0 50 30
vertex 50 50 30
vertex 0 50 40
endloop
endfacet
facet
outer loop
vertex 50 50 30
vertex 50 50 40
vertex 0 50 40
endloop
endfacet
facet
outer loop
vertex 0 0 30
vertex 0 50 30
vertex 0 0 40
endloop
endfacet
facet
outer loop
vertex 0 50 30
vertex 0 50 40
vertex 0 0 40
endloop
endfacet
facet
outer loop
vertex 50 0 30
vertex 50 0 40
vertex 50 50 30
endloop
endfacet
facet
outer loop
vertex 50 50 30
vertex 50 0 40
vertex 50 50 40
endloop
endfacet
facet
outer loop
vertex 10 10 40
vertex 40 10 40
vertex 10 40 40
endloop
endfacet
facet
outer loop
vertex 40 10 40
vertex 40 40 40
vertex 10 40 40
endloop
endfacet
facet
outer loop
vertex 10 10 50
vertex 10 40 50
vertex 40 10 50
endloop
endfacet
facet
outer loop
vertex 40 10 50
vertex 10 40 50
vertex 40 40 50
endloop
endfacet
facet
outer loop
vertex 10 10 40
vertex 10 10 50
vertex 40 10 40
endloop
endfacet
facet
outer loop
vertex 40 10 40
vertex 10 10 50
vertex 40 10 50
endloop
endfacet
facet
outer loop
vertex 10 40 40
vertex 40 40 40
vertex 10 40 50
endloop
endfacet
facet
outer loop
vertex 40 40 40
vertex 40 40 50
vertex 10 40 50
endloop
endfacet
facet
outer loop
vertex 10 10 40
vertex 10 40 40
vertex 10 10 50
endloop
endfacet
facet
outer loop
vertex 10 40 40
vertex 10 40 50
vertex 10 10 50
endloop
endfacet
facet
outer loop
vertex 40 10 40
vertex 40 10 50
vertex 40 40 40
endloop
endfacet
facet
outer loop
vertex 40 40 40
vertex 40 10 50
vertex 40 40 50
endloop
endfacet
endsolid
```

</details>

## Projects
### Short Project List
-  [x] Async Engine
-  [x] Perfect Interrupt Safety
-  [ ] Bloxd Game Engine
### Project Phases
- `Begin`: when a new rough idea is being made, BUT no progress is made on it
- `Discover`: when a new rough idea is being made, AND work has began on it
- `Pinpoint`: when the idea is being made alot clearer
- `Refine`: finding a method which enables the idea to come to reality
- `Utilise`: the code writing phase
- `Release`: when the code is done, and no more changes will need to be added to code, BUT changes to README still are occuring
- `End`: when the code is done AND no more changes will need to be added to ANY part of repo (INCLUDING README)
### Project List
<details>
  <summary>Open File</summary>

#### Working
> **Idea is Running smoothly without issues**
- Began: Projects which are in `Begin` phase
- Discovered: Projects which are in `Discover` phase
- Pinpointed: Projects which are in `Pinpoint` phase
- Refined: Projects which are in `Refine` phase
- Utilised: Projects which are in `Utilise` phase
- Released: Projects which are in `Released` phase
- Ended: Projects which are in `End` phase
#### Halted
> **Has gotten stuck at some point, but still finding progress**
- Began: halted at beginning work on idea
- Discover: halted at pinpointing exact idea
- Pinpointed: halted at finding a method
- Refined: 
- Utilised: 
- Released: 
- Ended: 
#### Awaiting
> **Idea has stopped progress at a stage for a given reason**
- Paused: Projects which are in any phase but currently paused due to other projects
- Postpone: Projects which are in `Refine` phase, but needed method doesnt exist yet
#### Resolves
> **Problems which have been resolved and sorted**
<!--i totally didnt steal that name from ASYNC ... -->

#### Rejects
> **Problems which have not been resolved yet**
<!-- ... its coincidence i swear -->

#### Given
- **Idea has been given to someone else to work on due to some criteria**

</details>
<!--
**GlitchHunterCoder/GlitchHunterCoder** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
