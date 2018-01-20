---
title: "モデル ファイルとマッピング ファイルを組み込みリソースにする方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 60c17ebbdd4b7e7f460855d4888a922da9c953d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>モデル ファイルとマッピング ファイルを組み込みリソースにする方法
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーションの埋め込みリソースとしてモデルおよびマッピング ファイルを展開することができます。 モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。 詳細については、「[Connection Strings (接続文字列)](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」をご覧ください。 既定では、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ツールによって、モデル ファイルとマッピング ファイルが組み込まれます。 モデル ファイルとマッピング ファイルを手動で定義する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アプリケーションと共にモデル ファイルとマッピング ファイルが組み込みリソースとして確実に配置されるように、この手順を使用します。  
  
> [!NOTE]
>  組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。  
  
### <a name="to-embed-model-and-mapping-files"></a>モデル ファイルとマッピング ファイルを組み込むには  
  
1.  **ソリューション エクスプ ローラー**、概念 (.csdl) ファイルを選択します。  
  
2.  **プロパティ**ペインで、設定**ビルド アクション**に**埋め込まれたリソース**です。  
  
3.  ストレージ (.ssdl) ファイルとマッピング (.msl) ファイルに対して手順 1. と手順 2. を繰り返します。  
  
4.  **ソリューション エクスプ ローラー**、App.config ファイルをダブルクリックし、変更、`Metadata`内のパラメーター、`connectionString`属性のいずれかに基づいて、次の形式。  
  
    -   `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=` `res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     詳細については、「[Connection Strings (接続文字列)](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」をご覧ください。  
  
## <a name="example"></a>例  
 埋め込みモデルとマッピング ファイルを参照して次の接続文字列、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)です。 この接続文字列は、プロジェクトの App.config ファイルに格納されています。  
  
  
  
## <a name="see-also"></a>参照  
 [モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [接続文字列を定義する方法](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [EntityConnection の接続文字列を作成する方法](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
