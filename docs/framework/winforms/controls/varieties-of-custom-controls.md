---
title: "さまざまなカスタム コントロール | Microsoft Docs"
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
  - "複合コントロール"
  - "コントロール [Windows フォーム], 複合"
  - "コントロール [Windows フォーム], 拡張"
  - "コントロール [Windows フォーム], 型"
  - "コントロール [Windows フォーム], ユーザー コントロール"
  - "カスタム コントロール [Windows フォーム]"
  - "拡張されたコントロール"
  - "ユーザー コントロール [Windows フォーム]"
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# さまざまなカスタム コントロール
.NET Framework では、新しいコントロールを開発および実装できます。  継承を通じて、使い慣れたユーザー コントロールや既存のコントロールの機能の拡張もできます。  また、それぞれ独自の描画を実行するカスタム コントロールを作成することもできます。  
  
 作成するコントロールの種類を決めるときに、判断に迷うことがあります。  ここでは、継承できる各種コントロールの違いを明らかにし、プロジェクトに合わせて特定の種類のコントロールを選択する方法について説明します。  
  
> [!NOTE]
>  Web フォームで使用するコントロールの作成については、「[Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)」を参照してください。  
  
## 基本コントロール クラス  
 <xref:System.Windows.Forms.Control> クラスは、Windows フォーム コントロールの基本クラスです。  このクラスは、Windows フォーム アプリケーションでのビジュアル表示に必要なインフラストラクチャを提供します。  
  
 <xref:System.Windows.Forms.Control> クラスは、Windows フォーム アプリケーションでビジュアル表示を実現するために次のタスクを実行します。  
  
-   ウィンドウ ハンドルを公開する。  
  
-   メッセージ ルーティングを管理する。  
  
-   マウス イベントとキーボード イベントの他にさまざまなユーザー インターフェイス イベントを提供する。  
  
-   高度なレイアウト機能を提供する。  
  
-   <xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A> など、ビジュアル表示に固有のさまざまなプロパティを格納する。  
  
-   Windows フォーム コントロールが Microsoft® ActiveX® コントロールとして機能するのに必要なセキュリティとスレッドのサポートを提供する。  
  
 基本クラスによってインフラストラクチャの大部分が提供されるため、Windows フォーム コントロールは比較的簡単に開発できます。  
  
## コントロールの種類  
 Windows フォームは、*複合*、*拡張*、*カスタム*の 3 種類のユーザー定義コントロールをサポートします。  次の各セクションでは、それぞれのコントロールについて説明し、プロジェクトで使用する種類を選択する際の推奨事項を示します。  
  
### 複合コントロール  
 複合コントロールは、Windows フォーム コントロールのコレクションをコモン コンテナーにカプセル化したものです。  この種のコントロールは、*ユーザー コントロール*とも呼ばれます。  コンテナーに含まれているコントロールは、*内在コントロール*と言います。  
  
 複合コントロールは、含まれる各 Windows フォーム コントロールに関連付けられている本来の機能をすべて保持し、選択したプロパティを公開および関連付けることができます。  また、開発者側の追加作業が不要な、既定のキーボード処理機能を数多く提供します。  
  
 たとえば、複合コントロールを作成して、データベースの顧客アドレス データを表示することもできます。  このコントロールには、データベース フィールドを表示するための <xref:System.Windows.Forms.DataGridView> コントロール、データ ソースへのバインディングを処理するための <xref:System.Windows.Forms.BindingSource> コントロール、およびレコード間を移動するための <xref:System.Windows.Forms.BindingNavigator> コントロールが含まれます。  データ バインディング プロパティを選択的に公開し、さらにコントロール全体をパッケージ化してアプリケーション間で再利用できます。  この種の複合コントロールの例については、「[方法 : Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)」を参照してください。  
  
 複合コントロールを作成するには、<xref:System.Windows.Forms.UserControl> クラスから派生します。  <xref:System.Windows.Forms.UserControl> 基本クラスは、子コントロールに対してキーボード ルーティング機能を提供し、複数の子コントロールを 1 つのグループとして機能させることができます。  詳細については、「[複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)」を参照してください。  
  
 **推奨事項**  
  
 <xref:System.Windows.Forms.UserControl> クラスからの継承は、次の場合に適しています。  
  
-   いくつかの Windows フォーム コントロールの機能を 1 つの再利用可能な単位に結合する場合。  
  
### 拡張コントロール  
 既存の Windows フォーム コントロールから継承したコントロールを派生できます。  この方法では、Windows フォーム コントロールの本来の機能をすべて保持しながら、カスタム プロパティやカスタム メソッドなどを追加して、それらの機能を拡張できます。  この方法では、基本コントロールの描画ロジックをオーバーライドし、そのユーザー インターフェイスの外観を変更して拡張できます。  
  
 たとえば、<xref:System.Windows.Forms.Button> コントロールから派生させることで、ユーザーがクリックした回数を追跡するコントロールを作成できます。  
  
 一部のコントロールでは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドすることにより、コントロールのグラフィカル ユーザー インターフェイスに独自の外観を与えることもできます。  クリックを追跡する拡張ボタンでは、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドして <xref:System.Windows.Forms.Control.OnPaint%2A> の基本実装を呼び出し、<xref:System.Windows.Forms.Button> コントロールのクライアント領域の一角にクリック回数を描画できます。  
  
 **推奨事項**  
  
 Windows フォーム コントロールからの継承は、次の場合に適しています。  
  
-   必要な機能のほとんどが、既存の Windows フォーム コントロールの機能と同じである場合。  
  
-   独自のグラフィカル ユーザー インターフェイスが必要でない場合。または、既存のコントロールに新しいグラフィカル ユーザー インターフェイスをデザインする場合。  
  
### カスタム コントロール  
 コントロールを作成する方法には、<xref:System.Windows.Forms.Control> から継承することにより、コントロールを最初から作成する方法もあります。  <xref:System.Windows.Forms.Control> クラスは、コントロールで必要とされるすべての基本的な機能 \(マウスやキーボードの処理イベントなど\) を提供しますが、コントロール固有の機能やグラフィカル インターフェイスは提供しません。  
  
 <xref:System.Windows.Forms.Control> クラスから継承してコントロールを作成する場合は、<xref:System.Windows.Forms.UserControl> コントロールや既存の Windows フォーム コントロールから継承する場合に比べて、より多くの検討と作業が必要です。  開発者に数多くの実装作業が委ねられるため、作成されるコントロールは、複合コントロールや拡張コントロールよりも柔軟で、ニーズにちょうど合うようコントロールを調整できます。  
  
 カスタム コントロールを実装するには、必要な機能別のコードだけでなく、コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> イベントのコードも記述する必要があります。  また、<xref:System.Windows.Forms.Control.WndProc%2A> メソッドをオーバーライドして、Windows メッセージを直接処理することもできます。  これは、最も強力なコントロールの作成方法ですが、この方法を活用するには、Microsoft Win32® API を十分に理解しておく必要があります。  
  
 カスタム コントロールの例として、アナログ時計の外観と動作を模した時計コントロールがあります。  カスタム描画を実行することにより、内部の <xref:System.Windows.Forms.Timer> コンポーネントからの <xref:System.Windows.Forms.Timer.Tick> イベントに応答して、時計の針を動かすことができます。  詳細については、「[方法 : シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)」を参照してください。  
  
 **推奨事項**  
  
 <xref:System.Windows.Forms.Control> クラスからの継承は、次の場合に適しています。  
  
-   コンポーネントに独自のグラフィカル表示を使用する場合。  
  
-   標準のコントロールにはない、独自の機能を実装する必要がある場合。  
  
### ActiveX コントロール  
 Windows フォーム インストラクチャは、Windows フォーム コントロールをホストするために最適化されていますが、代わりに ActiveX コントロールを使用することもできます。  Visual Studio では、このタスクに対するサポートが用意されています。  詳細については、「[方法 : Windows フォームに ActiveX コントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)」を参照してください。  
  
### ウィンドウなしのコントロール  
 Microsoft Visual Basic® 6.0 と ActiveX テクノロジは、*ウィンドウなしの*コントロールをサポートします。  ウィンドウなしのコントロールは、Windows フォームではサポートされません。  
  
## カスタムのデザイン体験  
 カスタムのデザイン時体験を実装する必要がある場合は、独自のデザイナーを作成できます。  複合コントロールの場合は、<xref:System.Windows.Forms.Design.ParentControlDesigner> クラスや <xref:System.Windows.Forms.Design.DocumentDesigner> クラスからカスタム デザイナー クラスを派生します。  拡張コントロールやカスタム コントロールの場合は、<xref:System.Windows.Forms.Design.ControlDesigner> クラスからカスタム デザイナー クラスを派生します。  
  
 <xref:System.ComponentModel.DesignerAttribute> を使用して、コントロールをデザイナーに関連付けます。  詳細については、「[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)」および「[How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)」を参照してください。  
  
## 参照  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [方法 : シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)