---
title: "モデリングとマッピング | Microsoft Docs"
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
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# モデリングとマッピング
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] の Entity Data Model ツールを使用すると、データベースまたはグラフィカルなモデルから .[edmx ファイル](http://msdn.microsoft.com/ja-jp/f4c8e7ce-1db6-417e-9759-15f8b55155d4)を作成し、データベースまたはモデルが変更されたときにこのファイルを更新できます。  
  
 Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。  Code First の開発に対しては、2 つの異なるシナリオがあります。  どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。  
  
 詳細については、「[概念モデルの作成とマッピング](http://go.microsoft.com/fwlink/?LinkId=235016)」を参照してください。  
  
 また [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] に含まれている EDM のジェネレーターを使用できます。  EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。  モデルとマッピングの内容を手動で作成することもできます。  詳細については、「[EDM ジェネレーター \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)」を参照してください。