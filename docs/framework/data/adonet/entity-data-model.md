---
title: "エンティティ データ モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1a1bdeffcc85383d241c277240187ede41401cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="entity-data-model"></a>エンティティ データ モデル
Entity Data Model (EDM) は、格納される形式に関係なく、データ構造を記述する一連の概念です。 EDM は、1976 年に Peter Chen により記述されたエンティティ リレーションシップ モデルを取り入れていますが、これを土台にして利用法が拡張されています。  
  
 EDM は、データを多くの形式で格納する場合につきまとう問題に対応しています。 たとえば、データをリレーショナル データベース、テキスト ファイル、XML ファイル、スプレッドシート、およびレポートに格納している企業について考えてみます。 この状況は、データ モデリング、アプリケーション設計、データ アクセスに深刻な問題を提示しています。 データ指向のアプリケーションを設計する場合、データ アクセス、ストレージ、およびスケーラビリティの効率性を損なうことなく、効率的で保守性に優れたコードを作成することが問題になります。 データがリレーショナル構造の場合は、データ アクセス、ストレージ、およびスケーラビリティの効率性が非常に高くなるものの、効率的で保守性に優れたコードを書くことが難しくなります。 データがオブジェクト構造の場合は、これが反対になり、効率的で保守性に優れたコードを作成しやすくなる一方で、データ アクセス、ストレージ、およびスケーラビリティの効率性が損なわれます。 これらの要因の間で適切なバランスを取れる場合でも、データを 1 つの形式から別の形式に移動する際に新しい問題が発生します。 Entity Data Model は、ストレージ スキーマに依存しないエンティティとリレーションシップでデータ構造を記述することで、これらの問題に対応しています。 このため、アプリケーションの設計と開発でデータの格納形式が問題になりません。 さらに、エンティティおよびリレーションシップによりアプリケーションで使用されるデータ構造 (格納形式ではなく) が記述されるため、アプリケーションの進化に伴ってこれらを進化させることができます。  
  
 `conceptual model` は、データ構造をエンティティおよびリレーションシップとして表現したもので、一般的には、EDM の概念を実装するドメイン固有言語 (DSL) で記述されます。 [概念スキーマ定義言語 (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)このようなドメイン固有言語の例に示します。 概念モデルで記述されるエンティティおよびリレーションシップは、アプリケーションにおけるオブジェクトとアソシエーションの抽象化と考えることができます。 これにより開発者は、ストレージ スキーマを気にすることなく概念モデルに集中でき、効率的で保守性に優れたコードを書けるようになります。 同時にストレージ スキーマの設計者は、データ アクセス、ストレージ、およびスケーラビリティの効率性に集中できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションのトピックでは、Entity Data Model の概念について説明します。 EDM を実装する DSL には、ここで解説した概念を含める必要があります。 なお、 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL を使用して概念モデルを定義します。 詳細については、次を参照してください。 [CSDL 仕様](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)です。  
  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Entity Data Model: 名前空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Entity Data Model: プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [アソシエーション End](../../../../docs/framework/data/adonet/association-end.md)  
  
 [アソシエーション End の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)  
  
 [アソシエーション セット End](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [アソシエーション型](../../../../docs/framework/data/adonet/association-type.md)  
  
 [複合型](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [外部キーのプロパティ](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [モデル宣言関数](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [モデル定義関数](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [プロパティ](../../../../docs/framework/data/adonet/property.md)  
  
 [参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>参照  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [.edmx ファイルの概要](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [CSDL 仕様](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
