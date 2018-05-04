---
title: 接続文字列を定義する方法
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 3f4de943392a8da9ebdf3743da2d6ef69d90d630
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-define-the-connection-string"></a>接続文字列を定義する方法
このトピックでは、概念モデルに接続するための接続文字列を定義する方法について説明します。 このトピックの内容がに基づいて、 [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)概念モデルです。 AdventureWorks Sales Model は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ドキュメントのタスク関連のトピック全般で使用されます。 このトピックは、既に構成されていることを想定しています、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] AdventureWorks Sales Model が定義されているとします。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルを手動で定義](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a)です。 このトピックの手順が記載されても[する方法: Entity Framework プロジェクトを手動で構成](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)です。  
  
> [!NOTE]
>  使用する場合、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)]ウィザード、Visual Studio プロジェクトが自動的に .edmx ファイルを生成され、構成を使用するプロジェクト、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。 詳細については、次を参照してください[する方法: Entity Data Model ウィザードを使用する。](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Entity Framework 接続文字列を定義するには  
  
-   プロジェクトのアプリケーション構成ファイル (app.config) を開き、次の接続文字列を追加します。  
  
  
  
     プロジェクトが、アプリケーション構成ファイルを持たない場合、1 つを選択して、追加できます**新しい項目の追加**から、**プロジェクト** メニューを選択すると、**全般**カテゴリで、選択すると**アプリケーション構成ファイル**、クリックして**追加**です。  
  
## <a name="see-also"></a>関連項目  
 [クイック スタート](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [方法: 新しい .edmx ファイルの作成](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
