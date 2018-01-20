---
title: "モデル宣言関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37c6b04fbea69f62aaf7bc148ee04ace5a5a349c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="model-declared-function"></a>モデル宣言関数
A*モデル宣言関数*関数は、概念モデルで宣言されていますが、その概念モデルで定義されていないです。 この関数は、ホスト環境またはストレージ環境で定義します。 たとえば、モデル宣言関数は、データベースに定義された関数にマップされ、これによって概念モデルにおけるサーバー側の機能が公開される場合があります。  
  
 モデル宣言関数の宣言には、次の情報が含まれます。  
  
-   関数の名前。 (必須)  
  
-   戻り値の型。 (オプション)。  
  
    > [!NOTE]
    >  戻り値が指定されていない場合、戻り値の型は void になります。  
  
-   パラメーター名と型を含むパラメーター情報。 (オプション)。  
  
## <a name="example"></a>例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 モデル宣言関数の 1 つの実装では、CSDL で、[関数インポート](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d)です。 次の CSDL は、関数インポート定義を含むエンティティ コンテナーを定義しています。 戻り値の型が指定されていないため、関数の戻り値の型は void になります。  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
