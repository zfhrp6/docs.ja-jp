---
title: "Walkthrough: Creating a Custom Dataflow Block Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, creating custom dataflow blocks"
  - "dataflow blocks, creating custom in TPL"
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Creating a Custom Dataflow Block Type
TPL データ フローのライブラリのさまざまな機能を有効にするには、いくつかのデータ フロー ブロック型がありますが、カスタム ブロック型を作成できます。  ここでは、カスタム動作を実装するデータ フロー ブロック型を作成する方法について説明します。  
  
## 必須コンポーネント  
 この説明を読む前に [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) を読み込みます。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## スライド式ウィンドウのデータ フローのブロックの定義  
 値を挿入し、スライド式ウィンドウで出力することはバッファーに格納されていることを必要とするデータ フロー アプリケーションがあるとします。  たとえば、入力値{0、1、2、3、4、5、および 3 のウィンドウ サイズに、スライド式ウィンドウのデータ フローのブロックが出力配列{0、1、2}、{1} {2、3、2、3、4 を生成および} {3、4、5\)。  以下のセクションでは、カスタム動作を実装するデータ フロー ブロック型を作成するには 2 とおりの方法について説明します。  最初の方法は、1 種類の伝達子ブロックに <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトと <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> オブジェクトの機能を結合するに <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> のメソッドを使用します。  2 番目の方法は <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> から派生し、カスタム動作を実行する既存の機能を組み合わせて使用するクラスを定義します。  
  
## スライド式ウィンドウのデータ フローのブロックを定義してカプセル化のメソッドを使用します。  
 次の例では、ソースとターゲットの伝達子ブロックを作成するために <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> のメソッドを使用します。  伝達子ブロックは、ソース ブロックとターゲット ブロックがデータの受信側と sender として機能するようにします。  
  
 この方法は、カスタム データ フロー機構を必要とするが、追加のメソッド、プロパティ、またはフィールドを提供する型が必要ではない場合に便利です。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## スライド式ウィンドウのデータ フローのブロックを定義して IPropagatorBlock からの派生  
 次の例は、`SlidingWindowBlock` クラスを示しています。  このクラスは <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> からデータ ソースおよびターゲットとして機能するように派生します。  前の例では、`SlidingWindowBlock` クラスは、既存のデータ フロー ブロック型に基づいています。  ただし、`SlidingWindowBlock` クラスは、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>と <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> インターフェイスで必要なメソッドを実装します。  これらのメソッドはすべて定義済みのなデータ フロー ブロック型のメンバーに作業を転送します。  たとえば、`Post` のメソッドは、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> オブジェクトである `m_target` データ メンバーと作業が遅延されます。  
  
 この方法は、カスタム データ フロー機構を必要とし、さらにメソッド、プロパティ、またはフィールドを提供する型が必要となる場合に便利です。  たとえば、`SlidingWindowBlock` クラスは、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> から <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> と <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> のメソッドを提供するために派生します。  `SlidingWindowBlock` クラスは、スライド式ウィンドウの要素の数を取得する `WindowSize` のプロパティを使用して、拡張機能を示します。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## 完全な例  
 次の例では、このチュートリアルの完全なコードを示しています。  、ブロックに記述し、そこから読み込み、結果をコンソールに出力するメソッドでスライド式ウィンドウのブロックを使用する方法を示します。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`SlidingWindowBlock.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`SlidingWindowBlock.vb`\) という名前で、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## 次の手順  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)