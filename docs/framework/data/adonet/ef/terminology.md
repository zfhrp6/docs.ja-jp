---
title: Entity Framework の用語
ms.date: 03/30/2017
ms.assetid: fa2a1bd1-6118-487b-8673-eebc66b92945
ms.openlocfilehash: 3b14ce6475befbf506e3927a1537e389baa0aa26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entity-framework-terminology"></a>Entity Framework の用語
このトピックで頻繁に参照用語の定義を[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ドキュメント。 追加情報を確認できる関連トピックへのリンクも示しています。  
  
|用語|定義|  
|----------|----------------|  
|関連付け|エンティティ型間のリレーションシップの定義。<br /><br /> 詳細については、次を参照してください。 [Association 要素 (CSDL)](http://msdn.microsoft.com/library/c305169a-8af7-432f-9ba7-800a163aed41)と[アソシエーション型](../../../../../docs/framework/data/adonet/association-type.md)です。|  
|関連付けセット|同じ型のアソシエーションのインスタンスの論理コンテナー。<br /><br /> 詳細については、次を参照してください。 [AssociationSet 要素 (CSDL)](http://msdn.microsoft.com/library/512cbb75-cebe-4f3f-970d-3419deeff684)と[アソシエーション セット](../../../../../docs/framework/data/adonet/association-set.md)です。|  
|Code First|Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。<br /><br /> ただし、Code First の開発の一部であること、 [Entity Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=234900)です。 Entity Framework 5.0 は .NET Framework の一部ではありませんが、.NET Framework 4.5 で構成されます。 Entity Framework 5.0 は、 [' Entity Framework'](http://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](http://go.microsoft.com/fwlink/?LinkId=232488)パッケージです。 詳細については、次を参照してください。 [Entity Framework リリースおよびバージョン管理](http://go.microsoft.com/fwlink/?LinkId=234899)です。|  
|コマンド ツリー|すべての共通プログラム表現[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]1 つまたは複数の式で構成されるクエリ。<br /><br /> 詳細については、次を参照してください。 [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)です。|  
|複合型|概念モデルで定義されている複合プロパティを表す [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] クラス。 複合型により、スカラー プロパティをエンティティ内で整理することができます。 複合オブジェクトは、複合型のインスタンスです。 詳細については、次を参照してください。 [ComplexType 要素 (CSDL)](http://msdn.microsoft.com/library/f1c2f311-9889-4b87-abd8-a94f322052e3)と[複合型](../../../../../docs/framework/data/adonet/complex-type.md)です。|  
|ComplexType|キー プロパティを持たないエンティティ型の非スカラー プロパティを表すデータ型の仕様。<br /><br /> 詳細については、次を参照してください。 [ComplexType 要素 (CSDL)](http://msdn.microsoft.com/library/f1c2f311-9889-4b87-abd8-a94f322052e3)と[複合型](../../../../../docs/framework/data/adonet/complex-type.md)です。|  
|概念モデル|[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] のアプリケーションのドメインにおけるエンティティ型、複合型、アソシエーション、エンティティ コンテナー、エンティティ セット、およびアソシエーション セットの抽象的な仕様。 概念モデルは、CSDL で .csdl ファイルに定義されます。<br /><br /> 詳細については、次を参照してください。[モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)です。|  
|.csdl ファイル|CSDL で表現された概念モデルを含む XML ファイル。|  
|概念スキーマ定義言語 (CSDL)|概念モデルのエンティティ型、関連付け、エンティティ コンテナー、エンティティ セット、および関連付けセットを定義するための XML ベースの言語。<br /><br /> 詳細については、次を参照してください。 [CSDL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)です。|  
|コンテナー|エンティティ セットとアソシエーション セットの論理的なグループ。<br /><br /> 詳細については、次を参照してください。 [EntityContainer 要素 (CSDL)](http://msdn.microsoft.com/library/06d03ecb-3b7a-4e7f-95d5-b95307d47a27)と[エンティティ コンテナー](../../../../../docs/framework/data/adonet/entity-container.md)です。|  
|同時実行|複数のユーザーが共有データに同時にアクセスや変更を行うことができるようにする処理。 既定では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、オプティミスティック同時実行制御モデルを実装しています。|  
|方向|一部のアソシエーションの非対称の性質を表します。 方向は、スキーマの `FromRole` 要素または `ToRole` 要素の `NavigationProperty` 属性と `ReferentialConstraint` 属性で指定されます。<br /><br /> 詳細については、次を参照してください。 [NavigationProperty 要素 (CSDL)](http://msdn.microsoft.com/library/5829a238-a50e-4c81-901d-7b54fc00f27e)と[ナビゲーション プロパティ](../../../../../docs/framework/data/adonet/navigation-property.md)です。|  
|一括読み込み|関連オブジェクトの特定のセットを、クエリで明示的に要求されたオブジェクトと共に読み込むプロセス。|  
|.edmx ファイル|概念モデル (CSDL)、ストレージ モデル (SSDL)、および概念モデルとストレージ モデルの間のマッピング (MSL) を含む XML ファイル。 .edmx ファイルは、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ツールによって作成されます。 詳細については、次を参照してください。 [.edmx ファイルの概要](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)です。|  
|end|アソシエーションに参加しているエンティティ。<br /><br /> 詳細については、次を参照してください。[終了要素 (CSDL)](http://msdn.microsoft.com/library/04f3c141-95bc-424b-989b-1c071b449e7c)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)です。|  
|entity|データ型を定義する際に基づくアプリケーションのドメインにおける概念。<br /><br /> 詳細については、次を参照してください。 [EntityType 要素 (CSDL)](http://msdn.microsoft.com/library/19562e9f-fd70-4b59-bc15-3e289cbb6054)と[エンティティ型](../../../../../docs/framework/data/adonet/entity-type.md)です。|  
|EntityClient|[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]、`EntityConnection`、`EntityCommand` などのクラスを含むストレージの影響を受けない `EntityDataReader` データ プロバイダー。 連携[!INCLUDE[esql](../../../../../includes/esql-md.md)]特定の記憶域に接続および[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]データ プロバイダーなど`SqlClient`です。<br /><br /> 詳細については、次を参照してください。 [Entity Framework の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)です。|  
|エンティティ コンテナー|指定された名前空間に実装されるエンティティ セットとアソシエーション セットを指定します。<br /><br /> 詳細については、次を参照してください。 [EntityContainer 要素 (CSDL)](http://msdn.microsoft.com/library/06d03ecb-3b7a-4e7f-95d5-b95307d47a27)と[エンティティ コンテナー](../../../../../docs/framework/data/adonet/entity-container.md)です。|  
|Entity Data Model (EDM)|格納される形式に関係なく、エンティティおよびリレーションシップとしてデータ構造を記述する一連の概念。<br /><br /> 詳細については、次を参照してください。 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)です。|  
|Entity Framework|開発者がデータ ソースの論理スキーマにマップされた概念モデルを使用できるようにすることで、データ指向のソフトウェア アプリケーションの開発をサポートするテクノロジ セット。<br /><br /> 詳細については、次を参照してください。 [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)です。|  
|エンティティ セット|指定された型とそのサブタイプのエンティティの論理コンテナー。 エンティティ セットは、データベース内のテーブルにマップされます。<br /><br /> 詳細については、次を参照してください。 [EntitySet 要素 (CSDL)](http://msdn.microsoft.com/library/ec56db77-718d-4c0e-adc9-f1d33c896287)と[エンティティ セット](../../../../../docs/framework/data/adonet/entity-set.md)です。|  
|Entity SQL|エンティティの概念スキーマを直接操作し、継承やリレーションシップなどの概念モデルの概念をサポートする、ストレージの影響を受けない SQL の言語。<br /><br /> 詳細については、次を参照してください。 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)します。|  
|エンティティ型|概念モデルでの定義に従ってエンティティを表す [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] クラス。 エンティティ型には、スカラー プロパティ、複合プロパティ、およびナビゲーション プロパティが含まれる場合があります。 オブジェクトは、エンティティ型のインスタンスです。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)です。|  
|EntityType|キーやプロパティの名前付きセットを含み、概念モデルまたはストレージ モデルの最上位項目を表すデータ型の仕様。<br /><br /> 詳細については、次を参照してください。 [EntityType 要素 (CSDL)](http://msdn.microsoft.com/library/19562e9f-fd70-4b59-bc15-3e289cbb6054)と[エンティティ型](../../../../../docs/framework/data/adonet/entity-type.md)です。|  
|明示的な読み込み|クエリがオブジェクトを返す場合、関連オブジェクトは同時に読み込まれません。 既定では、関連オブジェクトは、ナビゲーション プロパティの `Load` メソッドを使用して明示的に要求されるまで読み込まれません。|  
|外部キーの関連付け (アソシエーション)|外部キー プロパティで管理されるエンティティ間のアソシエーション。|  
|依存リレーションシップ|プリンシパル エンティティの主キーが依存エンティティの主キーの一部であるリレーションシップ。 このようなリレーションシップでは、プリンシパル エンティティが存在しないと、依存エンティティは存在できません。|  
|独立した関連付け (アソシエーション)|独立オブジェクトによって表され、追跡されるエンティティ間のアソシエーション。|  
|key|エンティティ型の一意のインスタンスを識別するために使用されるプロパティまたはプロパティ セットを指定するエンティティ型の属性。 オブジェクト レイヤーでは、<xref:System.Data.EntityKey> クラスで表現されます。<br /><br /> 詳細については、次を参照してください。[キー要素 (CSDL)](http://msdn.microsoft.com/library/0cdb1402-dbc7-4a04-a11e-5729cdf7431b)と[エンティティ キー](../../../../../docs/framework/data/adonet/entity-key.md)です。|  
|遅延読み込み|クエリがオブジェクトを返す場合、関連オブジェクトは同時に読み込まれません。 代わりに、ナビゲーション プロパティへのアクセス時に自動的に読み込まれます。|  
|[!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]|Visual c# および Visual Basic では、直接宣言的な方法で表現できるに走査、フィルター、およびプロジェクション操作を許可するクエリ演算子のセットを定義するクエリ構文。<br /><br /> 詳細については、次を参照してください。 [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)です。|  
|マップ|概念モデルの項目とストレージ モデルの項目の対応付けの指定。<br /><br /> 詳細については、次を参照してください。 [MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md)です。|  
|.msl ファイル|MSL で表現された概念モデルとストレージ モデルの間のマッピングを含む XML ファイル。|  
|マッピング仕様言語 (MSL)|概念モデルで定義された項目をストレージ モデルの項目に対応付ける XML ベースの言語。<br /><br /> 詳細については、次を参照してください。 [MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md)です。|  
|変更関数|データ ソースでデータを挿入、更新、および削除するために使用されるストアド プロシージャ。 この関数は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で生成されるコマンドの代わりに使用されます。 変更関数は、ストレージ モデルの `Function` 要素で定義されます。 [ModificationFunctionMapping](http://msdn.microsoft.com/library/b44b5b13-9937-448b-ba36-7a0cfefea782)要素が挿入、更新、および概念モデルで定義されているエンティティに対して操作を削除するには、この変更関数をマップします。|  
|多重度|アソシエーションによって定義されているリレーションシップの両側に存在できるエンティティの数。 カーディナリティとも呼ばれます。<br /><br /> 詳細については、次を参照してください。[終了要素 (CSDL)](http://msdn.microsoft.com/library/04f3c141-95bc-424b-989b-1c071b449e7c)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)です。|  
|Multiple-Entity-Sets-per-Type|1 つのエンティティ型を複数のエンティティ セットで定義できる機能。<br /><br /> 詳細については、次を参照してください。 [EntitySet 要素 (CSDL)](http://msdn.microsoft.com/library/ec56db77-718d-4c0e-adc9-f1d33c896287)と[する方法: 型ごとに複数のエンティティ セットでモデルを定義](http://msdn.microsoft.com/library/61aa4fca-5ac0-4f47-9bc8-46e8c2965ef7)です。|  
|ナビゲーション プロパティ|アソシエーションによって定義されている別のエンティティ型とのリレーションシップを表すエンティティ型のプロパティ。 ナビゲーション プロパティは、アソシエーションのもう一方の End での複数要素の接続性に応じて、関連オブジェクトを <xref:System.Data.Objects.DataClasses.EntityCollection%601> または <xref:System.Data.Objects.DataClasses.EntityReference%601> として返すために使用されます。<br /><br /> 詳細については、次を参照してください。 [NavigationProperty 要素 (CSDL)](http://msdn.microsoft.com/library/5829a238-a50e-4c81-901d-7b54fc00f27e)と[ナビゲーション プロパティ](../../../../../docs/framework/data/adonet/navigation-property.md)です。|  
|クエリ パス|オブジェクト クエリの実行時に返す関連オブジェクトを指定するパスの文字列表記。 クエリ パスは、<xref:System.Data.Objects.ObjectQuery%601.Include%2A> に対して <xref:System.Data.Objects.ObjectQuery%601> メソッドを呼び出すことによって定義されます。<br /><br /> 詳細については、次を参照してください。[関連オブジェクトの読み込み](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1)です。|  
|オブジェクト コンテキスト|概念モデルで定義したエンティティ コンテナーを表します。 基になるデータ ソースへの接続を含み、変更の追跡や ID 解決などのサービスを提供します。 オブジェクト コンテキストは、<xref:System.Data.Objects.ObjectContext> クラスまたは `DbContext` クラスのインスタンスで表されます。<br /><br /> `DbContext` 一部である、 [Entity Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=234900)です。 Entity Framework 5.0 は .NET Framework の一部ではありませんが、.NET Framework 4.5 で構成されます。 Entity Framework 5.0 は、 [' Entity Framework'](http://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](http://go.microsoft.com/fwlink/?LinkId=232488)パッケージです。 詳細については、次を参照してください。 [Entity Framework リリースおよびバージョン管理](http://go.microsoft.com/fwlink/?LinkId=234899)です。|  
|オブジェクト レイヤー|Entity Framework によって使用されるエンティティ型およびオブジェクト コンテキストの定義。|  
|オブジェクト クエリ|データをオブジェクトとして返す概念モデルに対してオブジェクト コンテキスト内で実行されるクエリ。<br /><br /> 詳細については、次を参照してください。[オブジェクト クエリ](http://msdn.microsoft.com/library/0768033c-876f-471d-85d5-264884349276)です。|  
|オブジェクト リレーショナル マッピング|リレーショナル データベースのデータをオブジェクト指向のソフトウェア アプリケーションで使用できるデータ型に変換する手法。<br /><br /> [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、ストレージ モデルで定義されたリレーショナル データを概念モデルで定義されたデータ型にマップして、オブジェクト リレーショナル マッピング サービスを提供します。<br /><br /> 詳細については、次を参照してください。[モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)です。|  
|オブジェクト サービス|によって提供されるサービス、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーション コードなどのエンティティに対して操作を可能にする[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]オブジェクト。|  
|永続化非依存オブジェクト|データ ストレージに関連するロジックが含まれていないオブジェクト。 POCO エンティティとも呼ばれます。|  
|POCO|Plain Old CLR Object の略。 別のクラスから継承しないオブジェクト、またはインターフェイスを実装しないオブジェクト。|  
|POCO エンティティ|[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の、<xref:System.Data.Objects.DataClasses.EntityObject> または <xref:System.Data.Objects.DataClasses.ComplexObject> から継承しないエンティティ、または [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] インターフェイスを実装しないエンティティ。 多くの場合、POCO エンティティは、既存のドメイン オブジェクトで使用する、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーションです。 このようなエンティティは、永続化非依存性をサポートしています。 詳細については、次を参照してください。 [POCO エンティティの操作](http://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3)です。|  
|プロキシ オブジェクト|POCO クラスから派生し、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって生成されたオブジェクト。変更追跡と遅延読み込みをサポートするために使用されます。 詳細については、次を参照してください。 [POCO プロキシの作成のため要件](http://msdn.microsoft.com/library/dcdbf982-9b9d-4582-806a-64de4a1c03c8)です。|  
|参照制約|エンティティが他のエンティティと依存関係にあることを示す、概念モデルで定義された制約。 この制約は、依存エンティティのインスタンスが対応する主要エンティティのインスタンスなしでは存在できないことを意味します。<br /><br /> 詳細については、次を参照してください。 [ReferentialConstraint 要素 (CSDL)](http://msdn.microsoft.com/library/24f96a80-85b5-4f2e-a14c-0e3eb6796fa0)と[参照整合性制約](../../../../../docs/framework/data/adonet/referential-integrity-constraint.md)です。|  
|リレーションシップ|エンティティ間の論理的な関係。|  
|ロール|リレーションシップのセマンティクスを明確にするためにアソシエーションの両方の `End` に付けられた名前。<br /><br /> 詳細については、次を参照してください。[終了要素 (CSDL)](http://msdn.microsoft.com/library/04f3c141-95bc-424b-989b-1c071b449e7c)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)です。|  
|スカラー プロパティ|ストレージ モデルの単一のフィールドにマップされるエンティティのプロパティ。|  
|自己追跡エンティティ|スカラー プロパティ、複合プロパティ、およびナビゲーション プロパティの変更を報告できる、テキスト テンプレート変換ツールキット (T4) から構築されるエンティティ。|  
|単純型|概念モデルでプロパティを定義するために使用されるプリミティブ型。<br /><br /> 詳細については、次を参照してください。[概念モデル型 (CSDL)](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)と[Entity Data Model: プリミティブ データ型](../../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)です。|  
|分割されたエンティティ|ストレージ モデルの 2 つの別個の型にマップされる 1 つのエンティティ型。<br /><br /> 詳細については、次を参照してください。[する方法: 2 つのテーブルにマップされた単一のエンティティを使用してモデルを定義する](http://msdn.microsoft.com/library/01762517-e4ab-439d-99e6-564ab7d6f3ed)です。|  
|ストレージ モデル|リレーショナル データベースなど、サポートされているデータ ソースのデータの論理モデルの定義。 ストレージ モデルは、SSDL で .ssdl ファイルに定義されます。<br /><br /> 詳細については、次を参照してください。[モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)と[SSDL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md)です。|  
|.ssdl ファイル|SSDL で表現されたストレージ モデルを含む XML ファイル。|  
|ストア スキーマ定義言語 (SSDL)|一般的にデータベース スキーマに対応するストレージ モデルのエンティティ型、アソシエーション、エンティティ コンテナー、エンティティ セット、およびアソシエーション セットの定義に使用される XML ベースの言語。<br /><br /> 詳細については、次を参照してください。 [SSDL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md)です。|  
|table-per-hierarchy|あらゆる型の属性を 1 つのテーブル内の階層構造に含める、データベースにおける型階層のモデリング手法。|  
|table-per-type|一対一リレーションシップを持った複数のテーブルを使用して各種の型をモデリングする、データベースにおける型階層のモデリング手法。|  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)  
 [はじめに](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 [Entity Framework のリソース](../../../../../docs/framework/data/adonet/ef/resources.md)
