---
title: "visual スタイルが使用されているコントロールのレンダリング | Microsoft Docs"
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
  - "プロフェッショナルな外観, Windows フォーム コントロールでのレンダリング"
  - "テーマ, XP の Visual スタイル (Window フォームでの)"
  - "カスタム コントロール [Windows フォーム], レンダリング"
  - "カスタム コントロール [Windows フォーム], 描画"
  - "ビジュアル テーマ, レンダリング (Windows フォーム コントロールの)"
  - "ユーザー コントロール [Windows フォーム], 描画"
  - "ビジュアル テーマ, レンダリング (Windows フォーム コントロールの)"
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# visual スタイルが使用されているコントロールのレンダリング
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] は、視覚スタイルをサポートするオペレーティング システムでの、それらを使用したコントロールと他の Windows ユーザー インターフェイス \(UI\) 要素のレンダリングをサポートします。 このトピックでは、オペレーティング システムの現在の視覚スタイルを使用したコントロールと他の UI 要素のレンダリングに関して [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] でのいくつかのサポート レベルについて説明します。  
  
## 一般的なコントロールのクラスをレンダリングする  
 コントロールのレンダリングとは、コントロールのユーザー インターフェイスを描画することを意味します。<xref:System.Windows.Forms?displayProperty=fullName> 名前空間は、いくつかの一般的な Windows フォーム コントロールをレンダリングするための <xref:System.Windows.Forms.ControlPaint> クラスを提供します。 ただし、このクラスは従来の Windows スタイルでコントロールを描画するため、視覚スタイルが有効になったアプリケーションでカスタム コントロールを描画する際の一貫した UI エクスペリエンスの維持が困難になる可能性があります。  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] に含まれる <xref:System.Windows.Forms?displayProperty=fullName> 名前空間のクラスは、視覚スタイルを使用して一般的なコントロールのパーツと状態をレンダリングします。 これらの各クラスに含まれる `static` メソッドにより、オペレーティング システムの現在の視覚スタイルを使用して、特定の状態のコントロールまたはコントロールのパーツを描画します。  
  
 これらのクラスの一部は、視覚スタイルが使用可能かどうかに関係なく関連するコントロールを描画するように設計されています。 視覚スタイルが有効になっている場合、クラス メンバーは視覚スタイルを使用して関連するコントロールを描画します。視覚スタイルが無効になっている場合、クラス メンバーは、従来の Windows スタイルでコントロールを描画します。 次のようなクラスがこれに含まれます。  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 他のクラスは、視覚スタイルが使用可能な場合にのみ関連するコントロールを描画することができ、視覚スタイルが無効になっている場合、それらのメンバーは例外をスローします。 次のようなクラスがこれに含まれます。  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 これらのクラスを使用したコントロールの描画の詳細については、「[方法 : コントロールの描画クラスを使用する](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md)」を参照してください。  
  
## 視覚スタイル要素とレンダリング クラス  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 名前空間に含まれるクラスを使用して、視覚スタイルによってサポートされる任意のコントロールまたは UI 要素を描画したり、それらに関する情報を取得したりすることができます。 サポートされるコントロールには、<xref:System.Windows.Forms?displayProperty=fullName> 名前空間のレンダリング クラスを使用する一般的なコントロール \(前のセクションを参照してください\)、およびタブ コントロールや rebar コントロールなどの他のコントロールが含まれます。 他のサポートされる UI 要素には、**\[スタート\]** メニュー、タスクバー、ウィンドウの非クライアント領域のパーツなどがあります。  
  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 名前空間の主要なクラスは <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> と <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> です。<xref:System.Windows.Forms.VisualStyles.VisualStyleElement> は、視覚スタイルによってサポートされる任意のコントロールまたはユーザー インターフェイス要素を識別するための基盤クラスです。<xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 自体に加えて、<xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 名前空間には、視覚スタイルによってサポートされるコントロール、コントロール パーツ、その他の UI 要素のすべての状態の <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> を返す `static` プロパティを持つ <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> の多くの入れ子になったクラスが含まれています。  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> は、オペレーティング システムの現在の視覚スタイルによって定義される各 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> を描画したり、それらに関する情報を取得したりするメソッドを提供します。 取得可能な要素に関する情報には、既定のサイズ、背景の種類、色の定義などが含まれます。<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> は、Windows プラットフォーム SDK の Windows シェル部分からの視覚スタイル \(UxTheme\) API の機能をラップします。 詳細については、MSDN ライブラリ \([http:\/\/msdn.microsoft.com\/library](http://msdn.microsoft.com/library/)\) のプラットフォーム SDK 部分の「Windows XP ビジュアル スタイルの使用」を参照してください。  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> と <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> の使用方法の詳細については、「[方法 : visual スタイル要素を描画する](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md)」を参照してください。  
  
## 視覚スタイルを有効にする  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.0 用に作成されたアプリケーションの視覚スタイルを有効にするには、プログラマーが、ComCtl32.dll バージョン 6 以降をコントロールの描画に使用することを指定するアプリケーション マニフェストを含める必要があります。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.1 以降を使用してビルドされたアプリケーションは、<xref:System.Windows.Forms.Application> クラスの <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドを使用できます。  
  
## 視覚スタイルのサポートの確認  
 <xref:System.Windows.Forms.Application> クラスの <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> プロパティは、現在のアプリケーションが視覚スタイルを使用してコントロールを描画しているかどうかを示します。 カスタム コントロールを描画するときには、<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> の値を確認して、コントロールのレンダリングに視覚スタイルを使用する必要があるかどうかを判断できます。 次の表に、<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> が `true` を返すために満たす必要がある 4 つの条件を示します。  
  
|条件|ノート|  
|--------|---------|  
|オペレーティング システム視覚スタイルをサポートしている。|この条件を個別に確認するには、<xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> クラスの <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> プロパティを使用します。|  
|ユーザーがオペレーティング システムで視覚スタイルを有効にしている。|この条件を個別に確認するには、<xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> クラスの <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> プロパティを使用します。|  
|アプリケーションで視覚スタイルが有効になっている。|アプリケーションで視覚スタイルを有効にするには、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドを呼び出すか、ComCtl32.dll バージョン 6 以降をコントロールの描画に使用することを指定するアプリケーション マニフェストを使用します。|  
|アプリケーション ウィンドウのクライアント領域を描画するために視覚スタイルが使用されている。|この条件を個別に確認するには、<xref:System.Windows.Forms.Application> クラスの <xref:System.Windows.Forms.Application.VisualStyleState%2A> プロパティを使用し、その値が <xref:System.Windows.Forms.VisualStyles.VisualStyleState?displayProperty=fullName> または <xref:System.Windows.Forms.VisualStyles.VisualStyleState?displayProperty=fullName> になっていることを確認します。|  
  
 ユーザーが視覚スタイルの有効と無効を切り替えたり、1 つの視覚スタイルから別の視覚スタイルに切り替えたりしたときに、それを確認するには、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=fullName> または <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=fullName> イベントのハンドラーの <xref:Microsoft.Win32.UserPreferenceCategory?displayProperty=fullName> 値を確認します。  
  
> [!IMPORTANT]
>  ユーザーが視覚スタイルを有効にしたり切り替えたりしたときに、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> を使用してコントロールまたは UI 要素をレンダリングする場合は、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> イベントではなく <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベントを処理するときにこの処理を実行してください。<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> を処理するときに <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> クラスを使用した場合は、例外がスローされます。  
  
## 参照  
 [コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)