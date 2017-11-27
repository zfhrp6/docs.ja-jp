---
title: "LINQ to DataSet クエリのデバッグ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 964a4d051600621d581e05dcf6b518b2766e2750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet クエリのデバッグ
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] コードのデバッグをサポートしています。 ただし、デバッグの違いがある[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コードと非-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]マネージ コード。 ほとんどのデバッグ機能と[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントをステップ実行、ブレークポイントの設定、デバッガー ウィンドウに表示される結果を表示するなどです。 ただし、クエリの実行がデバッグ中に考慮すべきいくつかの副作用を遅延[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コードし、はエディット コンティニュを使用するには、いくつか制限があります。 このトピックに固有のデバッグの側面を説明します。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]と比較して非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]マネージ コード。  
  
## <a name="viewing-results"></a>結果の表示  
 結果を表示することができます、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]データヒント、ウォッチ ウィンドウと [クイック ウォッチ] ダイアログ ボックスを使用してステートメントです。 ソース ウィンドウで特定のクエリにポインターを置くと、データヒントが表示されます。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] の変数をコピーし、それを [ウォッチ] ウィンドウまたは [クイック ウォッチ] ダイアログ ボックスに貼り付けることができます。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、クエリが評価されるのは、実際にそのクエリが実行されたときです。作成または宣言した時点では評価されません。 これと呼ばれる*遅延実行*です。 したがって、それが評価されるまでは、クエリ変数に値は割り当てられません。 詳細については、次を参照してください。[で LINQ to DataSet クエリ](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)です。  
  
 デバッガーは、クエリの結果を表示するために、そのクエリを評価する必要があります。 表示するときに、この暗黙の評価が発生した、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]と、デバッガーでクエリの結果がいくつかの影響を考慮する必要があります。 クエリの評価には時間がかかります。 結果ノードを展開するときにも時間を要します。 クエリによっては繰り返し評価が実行され、パフォーマンスが著しく低下する場合があります。 さらに、データの値またはプログラムの状態が変わるという副作用が伴う場合もあります。 すべてのクエリに副作用があるわけではありません。 副作用を伴うことなく安全にクエリを評価できるかどうかを判断するには、クエリが実装されているコードを十分に理解する必要があります。 詳細については、次を参照してください。[副作用と式](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)です。  
  
## <a name="edit-and-continue"></a>エディット コンティニュ  
 エディット コンティニュがへの変更をサポートしていません[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 追加、削除、または変更する場合、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントではデバッグ セッション中に、ダイアログ ボックスを表示、変更がエディット コンティニュでサポートされていないを示すです。 このとき、変更を元に戻すか、デバッグ セッションを中止して編集済みのコードで新たなセッションを開始するかを選択できます。  
  
 さらに、編集し、続行が型やで使用されている変数の値の変更をサポートしていない、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントです。 この場合も、変更を元に戻すか、デバッグ セッションを中止して新たなセッションを開始するかを選択できます。  
  
 Visual c# で Visual Studio で使うことはできませんエディット コンティニュを含むメソッドのコードに対して、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。  
  
 Visual Studio で Visual basic で行うこともできますエディット コンティニュ非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]を含むメソッドであっても、コード、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 追加または前にコードを削除することができます、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントでは、行番号が変わる場合でも、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 エクスペリエンスのデバッグ、Visual Basic ではない[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]前と同じコードまま[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]が導入されました。 変更、追加、または削除することはできません、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ、ただし、変更を適用するデバッグを停止する場合を除き、します。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](/visualstudio/debugger/debugging-managed-code)  
 [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
