---
title: "方法 : コントロール クラスを継承する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdc4a5c7f721fd350f5c604d4529f05afd62a42c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-the-control-class"></a>方法 : コントロール クラスを継承する
Windows フォームで使用する完全なカスタム コントロールを作成する場合から継承する必要があります、<xref:System.Windows.Forms.Control>クラスです。 継承するときに、<xref:System.Windows.Forms.Control>を計画および実装の詳細を実行するオプションを提供するオプションの最大範囲とクラスが必要です。 継承する場合<xref:System.Windows.Forms.Control>コントロールの動作を実現する非常に基本的な機能を継承します。 本来の機能、<xref:System.Windows.Forms.Control>クラス、キーボードとマウスを介してユーザー入力の処理、境界とコントロールのサイズを定義、windows ハンドルを提供およびメッセージの処理とセキュリティを提供します。 描画機能 (ここではコントロールのグラフィカル インターフェイスを実際に表示する機能) や、ユーザーとやり取りするための特定の機能は含まれていません。 このような機能はすべて、カスタム コードによって提供する必要があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-a-custom-control"></a>カスタム コントロールを作成するには  
  
1.  新しい **Windows アプリケーション** プロジェクトまたは **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
2.  **[プロジェクト]** メニューの **[クラスの追加]** を選択します。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4.  F7 キーを押して、カスタム コントロールの**コード エディター**を開きます。  
  
5.  検索、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの呼び出しを除く空になります、<xref:System.Windows.Forms.Control.OnPaint%2A>基底クラスのメソッドです。  
  
6.  コントロールで使用するカスタム描画が組み込まれるように、コードを修正します。  
  
     コントロールのグラフィックスをレンダリングするコードの記述については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。  
  
7.  コントロールに組み込むカスタム メソッド、カスタム プロパティ、カスタム イベントを実装します。  
  
8.  コントロールを保存して、動作確認を行います。  
  
## <a name="see-also"></a>参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [方法: UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [方法: 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [方法: Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
