---
title: "Serialization | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Serialization
このトピックでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のシリアル化機能について説明します。  デザイン時のコード生成でシリアル化を追加する方法と、実行時の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のクラスのシリアル化の動作について説明します。  
  
 デザイン時には、次のいずれかの方法でシリアル化のコードを追加できます。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]で、**Serialization Mode** プロパティを **Unidirectional** に変更します。  
  
-   SQLMetal コマンド ラインに **\/serialization** オプションを追加します。  詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
## 概要  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が生成するコードには、遅延読み込み機能が既定で備わっています。  遅延読み込みは、中間層でデータを必要に応じて透過的に読み込むうえでは非常に便利です。  しかし、シリアル化のときには問題です。遅延読み込みが意図されているかどうかに関係なく、シリアライザーによって遅延読み込みが発生するためです。  具体的には、オブジェクトがシリアル化されるときには、遅延読み込みされるすべての外部参照の推移的閉包がシリアル化されます。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のシリアル化機能では、この問題に対処しています。これには主に、次の 2 つの方法が使用されます。  
  
-   <xref:System.Data.Linq.DataContext> のモードにより、遅延読み込みをオフにします \(<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>\)。  詳細については、「<xref:System.Data.Linq.DataContext>」を参照してください。  
  
-   コード生成のスイッチにより、生成するエンティティに <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=fullName> 属性および <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=fullName> 属性を生成します。  この方法と、シリアル化での遅延読み込みクラスの動作が、このトピックの主な話題です。  
  
### 定義  
  
-   *DataContract シリアライザー* : .NET Framework 3.0 以降のバージョンの WCF \(Windows Communication Framework\) コンポーネントが使用する既定のシリアライザーです。  
  
-   *単方向シリアル化* : 循環参照を防ぐために、一方向の関連付けプロパティのみを含む、シリアル化されたバージョンのクラスです。  慣例として、主キー\/外部キーのリレーションシップの親側のプロパティをシリアル化の対象としてマークします。  双方向の関連付けの反対側はシリアル化しません。  
  
     [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、シリアル化の種類として、単方向シリアル化のみがサポートされています。  
  
## コード例  
 次のコードは、Northwind サンプル データベースの典型的な `Customer` クラスおよび `Order` クラスを使用して、これらのクラスをシリアル化の属性で装飾するようすを示します。  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 次の例の `Order` クラスでは、簡略化のために、`Customer` クラスに関する逆関連付けのプロパティのみを示します。  循環参照を防ぐために、`DataMember` 属性はありません。  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### エンティティをシリアル化する方法  
 前のセクションで示したコードのエンティティは次のようにシリアル化できます。  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### 自己再帰的リレーションシップ  
 自己再帰的リレーションシップも同じパターンに従います。  外部キーに関する関連付けのプロパティには `DataMember` 属性がなく、親プロパティにはあります。  
  
 次のクラスには、自己再帰的リレーションシップが 2 つあります。Employee.Manager\/Reports と Employee.Mentor\/Mentees です。  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## 参照  
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)