---
title: "方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する
このトピックでは、[EDM ジェネレーター \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) ツールを使用してモデル ファイルとマッピング ファイルを検証する方法を示します。  詳細については、「[Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)」を参照してください。  
  
### EdmGen.exe を使用して School モデルを検証するには  
  
1.  School データベースを作成します。  詳細については、「[Creating the School Sample Database](http://msdn.microsoft.com/ja-jp/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)」を参照してください。  
  
2.  School モデルを生成します。  詳細については、「[方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
3.  コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```scr  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## 参照  
 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/ja-jp/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)   
 [How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/ja-jp/b18a9d16-e10b-4043-ba91-b632f85a2579)   
 [方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)