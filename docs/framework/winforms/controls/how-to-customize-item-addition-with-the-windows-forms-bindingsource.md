---
title: "方法 : Windows フォーム BindingSource を使用した項目の追加をカスタマイズする | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 新しい項目の作成"
  - "BindingSource コンポーネント [Windows フォーム], 項目の追加のカスタマイズ"
  - "例 [Windows フォーム], BindingSource コンポーネント"
  - "BindingSource コンポーネント [Windows フォーム], 例"
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム BindingSource を使用した項目の追加をカスタマイズする
<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して Windows フォーム コントロールをデータ ソースにバインドする場合、新しい項目の作成のカスタマイズが必要な場合があります。<xref:System.Windows.Forms.BindingSource> コンポーネントでは、通常は、バインドされたコントロールで新しい項目の作成が必要になる際に発生する <xref:System.Windows.Forms.BindingSource.AddingNew> イベントが提供されるため、これが簡単になります。 イベント ハンドラーは、カスタム動作が必要なものをすべて提供できます \(Web サービスでのメソッドの呼び出し、クラス ファクトリからの新しいオブジェクトの取得など\)。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.BindingSource.AddingNew> イベントを処理することで項目が追加された場合、追加をキャンセルすることはできません。  
  
## 使用例  
 次の例では、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して、<xref:System.Windows.Forms.DataGridView> コントロールをクラス ファクトリにバインドする方法を示します。 ユーザーが <xref:System.Windows.Forms.DataGridView> コントロールの新しい行をクリックすると、<xref:System.Windows.Forms.BindingSource.AddingNew> イベントが発生します。 イベント ハンドラーは新しい `DemoCustomer` オブジェクトを作成します。これは、<xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=fullName> プロパティに割り当てられます。 これにより、新しい `DemoCustomer` オブジェクトが <xref:System.Windows.Forms.BindingSource> コンポーネントの一覧に追加され、<xref:System.Windows.Forms.DataGridView> コントロールの新しい行に表示されます。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  また、「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [方法 : Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)