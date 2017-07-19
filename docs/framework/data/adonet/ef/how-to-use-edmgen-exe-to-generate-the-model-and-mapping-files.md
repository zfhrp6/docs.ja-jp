---
title: "方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する | Microsoft Docs"
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
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する
このトピックでは、EDM ジェネレーター \(EdmGen.exe\) ツールを使用して、School データベースに基づく次のファイルを生成する方法について説明します。  
  
-   概念モデル \(.csdl ファイル\)  
  
-   ストレージ モデル \(.ssdl ファイル\)  
  
-   概念モデルとストレージ モデル間のマッピング \(.msl ファイル\)  
  
-   Visual Basic または C\# のオブジェクト レイヤー コード  
  
-   ビュー ファイル  
  
 EdmGen.exe ツールでは、\/mode:FullGeneration を使用して上記のファイルを生成します。  EdemGen.exe コマンドの詳細については、「[EDM ジェネレーター \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)」を参照してください。  
  
 EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するように [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトを構成する必要もあります。  詳細については、「[How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/ja-jp/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)」を参照してください。  
  
> [!NOTE]
>  EdmGen.exe によって生成された概念モデルには、データベース内のすべてのオブジェクトが含まれています。  特定のオブジェクトだけを含んだ概念モデルを生成する場合は、Entity Data Model ウィザードを使用してください。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
### EdmGen.exe を使用して Visual Basic プロジェクト用の School モデルを生成するには  
  
1.  School データベースを作成します。  詳細については、「[Creating the School Sample Database](http://msdn.microsoft.com/ja-jp/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)」を参照してください。  
  
2.  コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
  
    ```  
  
### EdmGen.exe を使用して C\# プロジェクト用の School モデルを生成するには  
  
1.  School データベースを作成します。  詳細については、「[Creating the School Sample Database](http://msdn.microsoft.com/ja-jp/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)」を参照してください。  
  
2.  コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## 参照  
 [モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)   
 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/ja-jp/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)   
 [How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/ja-jp/b18a9d16-e10b-4043-ba91-b632f85a2579)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)   
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)