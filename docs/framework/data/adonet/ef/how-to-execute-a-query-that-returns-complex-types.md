---
title: "複合型を返すクエリの実行方法 | Microsoft Docs"
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
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 複合型を返すクエリの実行方法
このトピックでは、複合型プロパティを含むエンティティ型オブジェクトを返す [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。  
  
### この例のコードを実行するには  
  
1.  [AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) をプロジェクトに追加して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  .edmx ファイルをダブルクリックして、エンティティ デザイナーの [&#91;モデル ブラウザー&#93; ウィンドウ](http://msdn.microsoft.com/ja-jp/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd)にモデルを表示します。  エンティティ デザイナー画面で、`Contact` エンティティ型の `Email` プロパティと `Phone` プロパティを選択し、右クリックして **\[新しい複合型へのリファクター\]** を選択します。  
  
4.  選択した `Email` プロパティと `Phone` プロパティの新しい複合型が**モデル ブラウザー**に追加されます。  複合型には既定の名前が付きます。**プロパティ** ウィンドウで型の名前を `EmailPhone` に変更します。  また、新しい `ComplexProperty` プロパティが `Contact` エンティティ型に追加されます。  プロパティの名前を  に変更します。  
  
     Entity Data Model ウィザードを使用した複合型の作成と変更の詳細については、「[How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/ja-jp/5b2eb3b3-693d-42cb-b43a-405812d677eb)」および「[How to: Create and Modify Complex Types](http://msdn.microsoft.com/ja-jp/afb8e206-0ffe-4597-b6d4-6ab566897e1d)」を参照してください。  
  
## 使用例  
 次の例は、`Contact` オブジェクトのコレクションを返し、`Contact`  オブジェクトの 2 つのプロパティとして `ContactID` と `EmailPhoneComplexType` 複合型の値を表示するクエリを実行します。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]