---
title: "方法 : デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1752691b3cc6809f1a5da54a01e81de2d4037d19
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>方法 : デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する
Microsoft Outlook で使用される次のようなマルチペイン ユーザー インターフェイスを作成する次の手順で、**フォルダー**  ボックスの一覧、**メッセージ** ウィンドウで、および**プレビュー**ウィンドウです。 この方法は、主にコントロールをフォームにドッキングすることにより実現されます。  
  
 コントロールをドッキングするときは、親コンテナーの端にコントロールを固定するを決定します。 このため、設定した場合、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Right>コントロールの右エッジは、親コントロールの右端にドッキングされます。 さらに、ドッキングされたコントロールの端は、コンテナー コントロールの一致するようにサイズ変更されます。 方法の詳細については<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを参照してください[する方法: Windows フォームでのドッキング コントロール](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)です。  
  
 この手順では、配置で、<xref:System.Windows.Forms.SplitContainer>および他のコントロール、フォームではなく、アプリケーションの Microsoft Outlook を模倣する機能を追加します。  
  
 内のすべてのコントロールを配置するこのユーザー インターフェイスを作成する、<xref:System.Windows.Forms.SplitContainer>を含むコントロール、<xref:System.Windows.Forms.TreeView>左側のパネルのコントロールです。 右側のパネル、<xref:System.Windows.Forms.SplitContainer>コントロールには、2 つ目が含まれている<xref:System.Windows.Forms.SplitContainer>コントロールを<xref:System.Windows.Forms.ListView>上のコントロール、<xref:System.Windows.Forms.RichTextBox>コントロール。 これら<xref:System.Windows.Forms.SplitContainer>コントロールがフォーム上の他のコントロールの独立したサイズ変更を有効にします。 独自のカスタム ユーザー インターフェイスを作成するには、この手順の手法を適用することができます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>デザイン時に Outlook スタイルのユーザー インターフェイスを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  ドラッグ、<xref:System.Windows.Forms.SplitContainer>から制御、**ツールボックス**をフォームにします。 **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。  
  
3.  ドラッグ、<xref:System.Windows.Forms.TreeView>から制御、**ツールボックス**の左側のパネルに、<xref:System.Windows.Forms.SplitContainer>コントロール。 **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Left>を示す下向きの矢印をクリックすると、値エディターで左側のパネルをクリックします。  
  
4.  別のドラッグ<xref:System.Windows.Forms.SplitContainer>から制御、**ツールボックス**; の右側のパネルに配置すること、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームに追加します。 **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>と<xref:System.Windows.Forms.SplitContainer.Orientation%2A>プロパティを<xref:System.Windows.Forms.Orientation.Horizontal>です。  
  
5.  ドラッグ、<xref:System.Windows.Forms.ListView>から制御、**ツールボックス**、2 つ目の上側のパネルに<xref:System.Windows.Forms.SplitContainer>コントロールをフォームに追加します。 <xref:System.Windows.Forms.ListView> プロパティの <xref:System.Windows.Forms.SplitContainer.Dock%2A> コントロールを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
6.  ドラッグ、<xref:System.Windows.Forms.RichTextBox>から制御、**ツールボックス**、2 つ目の下部のパネルに<xref:System.Windows.Forms.SplitContainer>コントロール。 <xref:System.Windows.Forms.RichTextBox> プロパティの <xref:System.Windows.Forms.SplitContainer.Dock%2A> コントロールを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
     この時点では、アプリケーションを実行する場合は F5 キーを押した場合、3 部構成のユーザー インターフェイスであり、Microsoft Outlook のと似ていますが、フォームに表示されます。  
  
    > [!NOTE]
    >  内でスプリッターのいずれかにマウス ポインターを配置すると、<xref:System.Windows.Forms.SplitContainer>コントロール、内部の次元のサイズを変更することができます。  
  
     この時点でアプリケーションの開発、高度なユーザー インターフェイスを作成しました。 次の手順は、アプリケーション自体のプログラミングを進めるおそらく接続することによって、<xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>いくつかの種類のデータ ソースへのコントロールです。 コントロールをデータに接続する方法の詳細については、次を参照してください。[データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
