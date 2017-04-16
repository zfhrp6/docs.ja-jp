---
title: "方法 : データ バインドで発生するエラーと例外を処理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingSource コンポーネント [Windows フォーム], 処理 (エラーと例外を)"
  - "データ バインド, エラー処理"
  - "データ バインド, 例"
  - "エラー処理, データ バインド"
  - "エラー処理, 例"
  - "例 [Windows フォーム], エラー処理"
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : データ バインドで発生するエラーと例外を処理する
基になるビジネス オブジェクトをコントロールにバインドするときに、それらのビジネス オブジェクトで例外やエラーが発生することがよくあります。  特定の <xref:System.Windows.Forms.Binding> コンポーネント、<xref:System.Windows.Forms.BindingSource> コンポーネント、または <xref:System.Windows.Forms.CurrencyManager> コンポーネントの <xref:System.Windows.Forms.Binding.BindingComplete> イベントを処理することにより、これらのエラーや例外をインターセプトし、回復したり、エラー情報をユーザーに渡したりできます。  
  
## 使用例  
 データ バインディング操作時に発生するエラーと例外を処理する方法を次のコード例に示します。  ここでは、<xref:System.Windows.Forms.Binding> オブジェクトの <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=fullName> イベントを処理してエラーをインターセプトする方法を示します。  このイベントを処理してエラーと例外をインターセプトするには、バインディングの書式設定を有効にする必要があります。  バインディングの書式設定は、バインディングの作成時やバインディング コレクションへの追加時に有効にできます。また、<xref:System.Windows.Forms.Binding.FormattingEnabled%2A> プロパティを `true` に設定すると有効にできます。  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 コードの実行時に、部品名に空の文字列が入力されるか、部品番号に 100 未満の値が入力されると、メッセージ ボックスが表示されます。  これは、これらのテキスト ボックス バインディングの <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=fullName> イベントを処理した結果です。  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=fullName>   
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=fullName>   
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)