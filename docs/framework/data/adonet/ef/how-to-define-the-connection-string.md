---
title: "接続文字列を定義する方法 | Microsoft Docs"
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
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 接続文字列を定義する方法
このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。  このトピックには、[AdventureWorks Sales](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) 概念モデルが使用されています。  AdventureWorks Sales Model は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ドキュメントのタスク関連のトピック全般で使用されます。  このトピックでは、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の構成が済んでいること、および AdventureWorks Sales Model が定義済みであることを前提としています。  詳細については、「[How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/ja-jp/d4fd6864-f2a1-48f0-aa32-1e318775a99a)」を参照してください。  このトピックの手順は、「[How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/ja-jp/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)」にも記載されています。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトで [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ウィザードを使用した場合、自動的に .edmx ファイルが生成され、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトが構成されます。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
### Entity Framework 接続文字列を定義するには  
  
-   プロジェクトのアプリケーション構成ファイル \(app.config\) を開き、次の接続文字列を追加します。  
  
  
  
     プロジェクトにアプリケーション構成ファイルが存在しない場合は、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** を選択し、**\[全般\]** カテゴリの **\[アプリケーション構成ファイル\]** を選択して、**\[追加\]** をクリックすることによって追加できます。  
  
## 参照  
 [Quickstart](http://msdn.microsoft.com/ja-jp/0bc534be-789f-4819-b9f6-76e51d961675)   
 [How to: Create a New .edmx File](http://msdn.microsoft.com/ja-jp/beb8189e-e51c-4051-839c-9902c224abf2)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)