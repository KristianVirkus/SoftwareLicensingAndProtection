# Software Licensing and Protection
This document describes a software solution helping to manage software licencing parameters and to secure on-premise software deployments against piracy and unpermitted use. To achieve this goal, the use of asymmetric cryptography is an essential part of the concept.

## Introduction
The development of software oftentimes involves noticable effort by means of tooling and third-party library investments, infrastructure investments, time, and thus - if conducted commercially - salary. Commercially developed software is usually sold to raise funds in order to pay developers and create further products or services. Exceptions include software accompanying other products (e.g. hardware drivers), software developed for marketing purposes to increase sales of other products from the same company, or open source software developed by companies which earn money through other products or services anyway (e.g. support and maintenance contracts for the software).

Simplified, if a company requires to earn money from the software they develop, measures might be needed to fight software piracy and unpermitted use. Depending on the type of software, general conditions, and the software's target, different measures may be appropriate.

## This Implementation and Tampering Countermeasures
The solution presented by this project uses asymmetric cryptography to encrypt a structured licence file issued by the developer of the software. The private key is only known to the developer of the software while the public key is included in the deployed software binary files. Extraction and exchange of the public key is surely possible by some person with even few reverse engineering skills or possibly even with just the use of appropriate tools if the public key or other parameters are embedded into the software's binary files. Identifying and exchanging these information would allow to decrypt the developer-provided licence file and to provide an own file tampering the intended software licencing measures. Deploying these information separately would even more ease the procedure. Also strong-signing .NET assemblies does not prevent tampering. Therefore further measures should be taken to make this process harder and less automatable by existing tools which will reduce the number of people being able to perform the manipulation. This may include one or multiple of the following:
- custom algorithms to extract the public key or other parameters from binary files,
- .NET assemblies obfuscation,
- disguise licencing libraries by merging them into the main binary,
- executable packing
- bootstrapping further application logic from self-signed assemblies

## Classification and Domain
In order to classify the software protection solution developed by this project one may assume there are several different levels of protection against software piracy and unpermitted use. The following list mentions them - ordered by estimated effectiveness - along with methods to break the protection measures and countermeasures. With increasing effectiveness, the user aversion and technical problems also potentially increase:
- no software protection at all / just copy / e.g. custom diskette drive sector sizes
- product keys / reverse engineering for key verification algorithm, key generator creation / obfuscation to complicate key generator development
- encrypted licence files / reverse engineering to replace cryptographic parameters / enforce internet activation
- internet activation / query redirection (hosts file) / enforce secure connection and apply measures to protect from reverse engineering and replacement of cryptographic parameters
- hardware protection (dongles) / SaaS / apply measures to 

The software protection solution developed by this project is definitely not at the top of the most effective measures ever implemented like relying on dedicated licencing and anti-piracy hardware dongles, but it may suit a software developer's needs if:
- the number of licences sold is low enough such that there is no "public interest" into illegal copies of the developed software and thus probably no cracker will put effort into breaking the measures applied,
- the software is distributed by sales multipliers which are not rated absolutely trustworth,
- other software protection solutions do not fit the needs

## Further concepts to be considered
- online software activation and licencing
- securing licence files
- including required hardware environment aspects (e.g. immutable USB thumb drive serial numbers) in licence information
- internal/external online licencing self-service; also hides private cryptography parameters from unauthorised developers; allows authorised customers to issue licences themselves with automated billing
- perpetual licencing by supporting multiple licence files, replacing, complementing, or invalidating each other

## Copyright and Licence
Copyright (c) 2016 by Kristian Virkus
Licenced under "Apache License 2.0". Please see "LICENSE" file.

## Contributions
Contribution rules have not been defined yet.

## References
None yet.

## Notes
The project name, file names, identifiers, and such are named in American English while all prose like documentation or source code comments are written in British English. The former is done for conformance reasons, the latter is done for personal preference.
