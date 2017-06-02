---
title: "方法 : Windows フォームのコントロールを作成する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 作成"
  - "カスタム コントロール [Windows フォーム], 作成"
  - "UserControl クラス, Windows フォーム"
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームのコントロールを作成する
コントロールは、ユーザーとプログラムの間のグラフィカルなリンクとして機能します。  コントロールには、データの提供や処理、ユーザー入力の受け付け、イベントへの応答など、ユーザーとアプリケーションを結び付けるさまざまな機能があります。  コントロールは、本質的には、グラフィカル インターフェイスを持つコンポーネントです。このため、ユーザーとプログラムの間のやり取りを処理するだけでなく、コンポーネントが実行するすべての機能も備えています。  コントロールは特定の目的のために作成されたもので、プログラミング作業の一部としてコントロールを作成します。  これを踏まえたコントロールの作成手順の概要を以下に示します。  各手順に関連するトピックへのリンクもあります。  
  
> [!NOTE]
>  Web フォームで使用するカスタム コントロールを作成する場合は、「[Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールを作成するには  
  
1.  コントロールの目的、またはアプリケーションにおけるコントロールの役割を決定します。  次の点を考慮します。  
  
    -   どのようなグラフィカル インターフェイスが必要か。  
  
    -   ユーザーとコントロールの間のどのようなやり取りを処理するか。  
  
    -   必要な機能を持つ既存のコントロールがあるか。  
  
    -   いくつかの Windows フォーム コントロールを組み合わせることで必要な機能が得られるか。  
  
2.  コントロールのオブジェクト モデルが必要な場合は、オブジェクト モデルで機能を分散する方法を決定し、コントロールとサブオブジェクトの間で機能を分割します。  オブジェクト モデルは、複雑なコントロールをプランニングする場合や、いくつかの機能を含める場合などに役立ちます。  
  
3.  必要なコントロールの種類 \(ユーザー コントロール、カスタム コントロール、継承された Windows フォーム コントロールなど\) を決定します。  詳細については、「[コントロールの種類に関するアドバイス](../../../../docs/framework/winforms/controls/control-type-recommendations.md)」および「[さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)」を参照してください。  
  
4.  必要な機能をコントロール \(およびそのサブオブジェクトまたは下位構造\) のプロパティ、メソッド、およびイベントとして表現し、適切なアクセス レベル \(パブリックやプロテクトなど\) を割り当てます。  
  
5.  コントロールにカスタム描画が必要な場合は、そのためのコードを追加します。  詳細については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。  
  
6.  コントロールが <xref:System.Windows.Forms.UserControl> を継承している場合、コントロール プロジェクトをビルドし、**UserControl テスト コンテナー**で実行することによって、コントロールの実行時の動作をテストできます。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
7.  また、Windows アプリケーションなどの新しいプロジェクトを作成し、コンテナー内に配置することで、コントロールをテストしてデバッグすることもできます。  この処理については、「[チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)」で説明します。  
  
8.  機能を追加するごとに、新しい機能を実行するための機能をテスト プロジェクトに追加します。  
  
9. テストを繰り返して、デザインを微調整します。  
  
10. コントロールをパッケージ化して配置します。  詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)」を参照してください。  
  
## 参照  
 [チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [チュートリアル : Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [方法 : UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [方法 : コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [方法 : 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)