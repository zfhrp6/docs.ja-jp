---
title: "Entity Data Model キーの概念 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Data Model キーの概念
Entity Data Model \(EDM\) では、*エンティティ型*、*アソシエーション型*、および*プロパティ*という 3 つの主要概念を使用してデータ構造を記述します。  これらは、EDM の実装においてデータ構造を記述する上で最も重要な概念です。  
  
## エンティティ型  
 [エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)は、Entity Data Model でデータ構造を記述するために不可欠な構成要素です。  概念モデルでは、エンティティ型は、[プロパティ](../../../../docs/framework/data/adonet/property.md)から構成され、ビジネス アプリケーションの顧客や注文のように、トップレベル概念の構造を記述します。  コンピューター プログラムのクラス定義がクラスのインスタンスのテンプレートになるように、エンティティ型はエンティティのテンプレートになります。  エンティティは、特定のオブジェクト \(特定の顧客や注文など\) を表します。  各エンティティに対して、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)内の[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)を一意にする必要があります。  エンティティ セットは、特定のエンティティ型のインスタンスのコレクションです。  エンティティ セット \(および[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)\) は[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)に論理的にグループ化されます。  
  
 エンティティ型では継承がサポートされており、1 つのエンティティ型を別のエンティティ型から派生させることができます。  詳細については、「[Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)」を参照してください。  
  
## アソシエーション型  
 [アソシエーション型](../../../../docs/framework/data/adonet/association-type.md) \(アソシエーションとも呼ばれます\) は、Entity Data Model でリレーションシップを記述するために不可欠な構成要素です。  概念モデルでは、アソシエーションが 2 つのエンティティ型 \(Customer や Order など\) の間のリレーションシップを表します。  すべてのアソシエーションには、アソシエーションに含まれるエンティティ型を指定する 2 つの[アソシエーション End](../../../../docs/framework/data/adonet/association-end.md) があります。  各アソシエーション End には、アソシエーションのその End に存在できるエンティティ数を示す[アソシエーション End の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)も指定する必要があります。  アソシエーション End の多重度には、1 \(1\)、ゼロか 1 \(0..1\)、または多数 \(\*\) の値を指定することができます。  アソシエーションの 1 つの End にあるエンティティには、エンティティ型で公開されている場合、[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)または外部キーからアクセスできます。  詳細については、「[外部キーのプロパティ](../../../../docs/framework/data/adonet/foreign-key-property.md)」を参照してください。  
  
 アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション \(Customer のインスタンスと Order のインスタンスの間のアソシエーションなど\) を表します。  アソシエーション インスタンスは、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)に論理的にグループ化されます。  アソシエーション セット \(および[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)\) は[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)に論理的にグループ化されます。  
  
## プロパティ  
 [エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)には、その構造と特性を定義する[プロパティ](../../../../docs/framework/data/adonet/property.md)が含まれます。  たとえば、Customer エンティティ型には、CustomerId、Name、Address などのプロパティがあります。  
  
 概念モデルのプロパティは、コンピューター プログラムのクラスに定義されるプロパティに似ています。  クラスのプロパティがクラスの構造を定義し、オブジェクトに関する情報を伝達するのと同様に、概念モデルのプロパティはエンティティ型の構造を定義し、エンティティ型のインスタンスに関する情報を伝達します。  
  
 プロパティには、プリミティブ データ \(文字列、整数、ブール値など\) または構造化データ \(複合型\) を含めることができます。  詳細については、「[Entity Data Model: プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)」を参照してください。  
  
## 概念モデルの表現  
 *概念モデル*は、一部のデータの構造をエンティティおよびリレーションシップとして表現したものです。  概念モデルを表現する 1 つの手段として、ダイアグラムを使用することができます。  下のダイアグラムは、3 つのエンティティ型 \(`Book`、`Publisher`、および `Author`\) と 2 つのアソシエーション \(`PublishedBy` および `WrittenBy`\) の概念モデルを表しています。  
  
 ![ナビゲーション プロパティが含まれるモデル](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 しかし、この表現には、モデルに関する詳細を伝える上でいくつかの欠点があります。  たとえば、プロパティ型とエンティティ セットの情報はダイアグラムに示されていません。  ドメイン固有言語 \(DSL\) を使用すると、概念モデルの詳細情報をさらに明確に伝えることができます。  [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれる XML ベースの DSL を使用して概念モデルを定義します。  以下に、上のダイアグラムに示されている概念モデルの CSDL 定義を示します。  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## 参照  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)