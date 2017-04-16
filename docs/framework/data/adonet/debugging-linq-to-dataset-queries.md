---
title: "Debugging LINQ to DataSet Queries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Debugging LINQ to DataSet Queries
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] コードのデバッグをサポートしています。  ただし、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] コードのデバッグと [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 以外のマネージ コードのデバッグとでは若干違いがあります。ステップ実行、ブレークポイントの設定、デバッガー ウィンドウでの結果の確認など、ほとんどのデバッグ機能は [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ステートメントでも使用できます。  ただし、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] コードをデバッグする際は、クエリの遅延実行によって生じる副作用を考慮する必要があります。また、エディット コンティニュにも使用上の制限がいくつかあります。  このトピックでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] でデバッグを行う場合に固有の事項について、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 以外のマネージ コードと比較しつつ説明します。  
  
## 結果の表示  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ステートメントの結果は、データヒント、\[ウォッチ\] ウィンドウ、\[クイック ウォッチ\] ダイアログ ボックスを使用して確認できます。  ソース ウィンドウで特定のクエリにポインターを置くと、データヒントが表示されます。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] の変数をコピーし、それを \[ウォッチ\] ウィンドウまたは \[クイック ウォッチ\] ダイアログ ボックスに貼り付けることができます。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、クエリが評価されるのは、作成したときでも宣言したときでもなく、実際にそのクエリが実行されたときです。  これを*遅延実行*といいます。  したがって、それが評価されるまでは、クエリ変数に値は割り当てられません。  詳細については、「[Queries in LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)」を参照してください。  
  
 デバッガーは、クエリの結果を表示するために、そのクエリを評価する必要があります。  この暗黙的な評価は、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のクエリ結果をデバッガーで表示したときに実行されます。この点には、考慮する必要のあるいくつかの影響があります。  クエリの評価には時間がかかります。  結果ノードを展開するときにも時間を要します。  クエリによっては繰り返し評価が実行され、パフォーマンスが著しく低下する場合があります。  さらに、データの値またはプログラムの状態が変わるという副作用が伴う場合もあります。  すべてのクエリに副作用があるわけではありません。  副作用を伴うことなく安全にクエリを評価できるかどうかを判断するには、クエリが実装されているコードを十分に理解する必要があります。  詳細については、「[副作用と式](../Topic/Side%20Effects%20and%20Expressions.md)」を参照してください。  
  
## エディット コンティニュ  
 エディット コンティニュは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリに対する変更をサポートしません。  デバッグ セッション中に [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ステートメントを追加、削除、または変更しようとした場合、エディット コンティニュでサポートされない変更であることを伝えるダイアログ ボックスが表示されます。  このとき、変更を元に戻すか、デバッグ セッションを中止して編集済みのコードで新たなセッションを開始するかを選択できます。  
  
 また、エディット コンティニュでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ステートメントで使用されている変数の型または値を変更することはできません。  この場合も、変更を元に戻すか、デバッグ セッションを中止して新たなセッションを開始するかを選択できます。  
  
 Visual Studio の Visual C\# では、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリを含んだメソッドのコードに対して、エディット コンティニュを使用することはできません。  
  
 Visual Studio の Visual Basic では、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリを含んだメソッドであっても、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 以外のコードであればエディット コンティニュを使用できます。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ステートメントの前にコードを追加したり削除したりすることもできます。その変更によって [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリの行番号に影響が生じる場合でも可能です。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 以外のコードの Visual Basic デバッグは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] が導入される前と同じように動作します。  ただし、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリの変更、追加、または削除を行う場合は、デバッグを停止してから変更を適用する必要があります。  
  
## 参照  
 [マネージ コードのデバッグ](../Topic/Debugging%20Managed%20Code.md)   
 [Programming Guide](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)