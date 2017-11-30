---
title: "チュートリアル: カスタム データフロー ブロックの型の作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>チュートリアル: カスタム データフロー ブロックの型の作成
TPL データ フロー ライブラリは、さまざまな機能を有効にするいくつかのデータ フロー ブロックの型を提供しますが、カスタムのブロックの型を作成することもできます。 このドキュメントでは、カスタム動作を実装するデータフロー ブロックの型を作成する方法について説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 読み取り[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)このドキュメントを読む前にします。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="defining-the-sliding-window-dataflow-block"></a>スライディング ウィンドウのデータ フロー ブロックを定義します。  
 入力値のバッファリング、スライディング ウィンドウで、出力が必要なデータフロー アプリケーションを検討してください。 たとえば、{0、1、2、3、4, 5} の入力値と 3 つのウィンドウ サイズは、スライディング ウィンドウのデータ フロー ブロックが生成されます {0、1, 2} の出力配列 {1、2、3}、{2、3、4} と {3, 4, 5}。 次のセクションでは、このカスタム動作を実装するデータフロー ブロックの型を作成する 2 つの方法について説明します。 最初の手法を使用して、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>の機能を結合する方法、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクトおよび<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>オブジェクトを 1 つの伝達子ブロックにします。 派生するクラスを定義する 2 番目の手法<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>カスタム動作を実行する既存の機能を組み合わせたものとします。  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>使用して、スライディング ウィンドウのデータ フロー ブロックを定義するメソッドをカプセル化  
 次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>メソッドをターゲットとソースから伝達子ブロックを作成します。 伝達子ブロックには、ソース ブロックと受信者およびデータの送信者として機能する、ターゲット ブロックが実行できます。  
  
 この手法は、カスタム データ フロー機能が必要な追加のメソッド、プロパティ、またはフィールドを提供する型を必要としない場合に便利です。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>スライディング ウィンドウのデータ フロー ブロックを定義する IPropagatorBlock から派生します。  
 次の例は、`SlidingWindowBlock`クラスです。 このクラスから派生<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>ソースとデータのターゲットの両方として動作できるようにします。 前の例のように、`SlidingWindowBlock`クラスは、既存のデータ フロー ブロックの型に基づいて構築されています。 ただし、`SlidingWindowBlock`もクラスで必要なメソッド、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>、および<xref:System.Threading.Tasks.Dataflow.IDataflowBlock>インターフェイスです。 これらのメソッドをすべて転送は、定義済みのデータ フロー ブロックの型のメンバーに動作します。 たとえば、`Post`メソッドへの作業を延期する、`m_target`データ メンバーは、これはでも、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>オブジェクト。  
  
 この手法は、カスタム データ フロー機能を必要としも 追加のメソッド、プロパティ、またはフィールドを提供する型が必要な場合に便利です。 たとえば、`SlidingWindowBlock`からも派生<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>に提供できるように、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>と<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>メソッドです。 `SlidingWindowBlock`クラスが提供することによっても拡張機能を示します、`WindowSize`プロパティで、スライディング ウィンドウ内の要素の数を取得します。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>完全な例  
 次の例は、このチュートリアルのコード全体を示しています。 また、ブロックを書き込みますから読み取り、結果をコンソールに出力するメソッドで、両方スライディング ウィンドウ ブロックを使用する方法も示します。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付けます`SlidingWindowBlock.cs`(`SlidingWindowBlock.vb`の[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) および Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
