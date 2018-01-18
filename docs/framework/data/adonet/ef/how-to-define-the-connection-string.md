---
title: "接続文字列を定義する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7c17029dade53c724420fa5604ba3448ce6a6ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-define-the-connection-string"></a>接続文字列を定義する方法
このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。 このトピックの内容がに基づいて、 [AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)概念モデルです。 AdventureWorks Sales Model は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ドキュメントのタスク関連のトピック全般で使用されます。 このトピックは、既に構成されていることを想定しています、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] AdventureWorks Sales Model が定義されているとします。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルを手動で定義](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a)です。 このトピックの手順が記載されても[する方法: Entity Framework プロジェクトを手動で構成](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)です。  
  
> [!NOTE]
>  [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] プロジェクトで [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] ウィザードを使用した場合、自動的に .edmx ファイルが生成され、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトが構成されます。 詳細については、次を参照してください[する方法: Entity Data Model ウィザードを使用する。](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Entity Framework 接続文字列を定義するには  
  
-   プロジェクトのアプリケーション構成ファイル (app.config) を開き、次の接続文字列を追加します。  
  
  
  
     プロジェクトが、アプリケーション構成ファイルを持たない場合、1 つを選択して、追加できます**新しい項目の追加**から、**プロジェクト** メニューを選択すると、**全般**カテゴリで、選択すると**アプリケーション構成ファイル**、クリックして**追加**です。  
  
## <a name="see-also"></a>参照  
 [クイック スタート](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [方法: 新しい .edmx ファイルの作成](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
