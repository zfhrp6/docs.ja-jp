---
title: "方法 : クリックとダブルクリックを識別する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b407f7c00454b0a14b4c90694d015b38ffd72ef
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>方法 : クリックとダブルクリックを識別する
通常、1 回の*クリック*によってユーザー インターフェイス (UI) のアクションが開始され、*ダブルクリック*によってそのアクションが拡張されます。 たとえば、通常、1 回のクリックで項目が選択され、ダブルクリックでその項目が編集されます。 ただし、Windows フォームのクリック イベントでは、クリックとダブルクリックによって矛盾するアクションが実行されるようなシナリオには簡単に対応できません。それは、<xref:System.Windows.Forms.Control.Click> イベントや <xref:System.Windows.Forms.Control.MouseClick> イベントに結び付けられたアクションが、<xref:System.Windows.Forms.Control.DoubleClick> イベントや <xref:System.Windows.Forms.Control.MouseDoubleClick> イベントに結び付けられたアクションの前に実行されるためです。 ここでは、この問題の 2 つの解決方法について説明します。 1 つの解決方法は、ダブルクリック イベントを処理し、クリック イベントの処理のアクションをロールバックすることです。 まれに、クリック動作およびダブルクリック動作のシミュレートが必要になることがあります。その場合は、<xref:System.Windows.Forms.Control.MouseDown> イベントを処理し、<xref:System.Windows.Forms.SystemInformation> クラスの <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> プロパティと <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> プロパティを使用します。 クリック間の時間を測定し、<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> の値に到達する前に 2 回目のクリックが発生しており、かつ <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> によって定義された四角形内でクリックが行われている場合は、ダブルクリック アクションが実行されます。それ以外の場合は、クリック アクションが実行されます。  
  
### <a name="to-roll-back-a-click-action"></a>クリック アクションをロールバックするには  
  
-   対象のコントロールに標準のダブルクリック動作が含まれることを確認します。 含まれない場合は、<xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを使用してコントロールでダブルクリックを有効にします。 ダブルクリック イベントを処理して、ダブルクリック アクションを実行するだけでなく、クリック アクションをロールバックします。 ダブルクリックが有効になっているカスタム ボタンを作成する方法と、ダブルクリック イベント処理コード内でクリック アクションをロールバックする方法を次のコード例に示します。  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>MouseDown イベントでのクリックを区別するには  
  
-   <xref:System.Windows.Forms.Control.MouseDown> イベントを処理し、適切な <xref:System.Windows.Forms.SystemInformation> プロパティと <xref:System.Windows.Forms.Timer> コンポーネントを使用して、クリックが発生した場所および間隔を確認します。 クリックとダブルクリックのどちらが発生したかに応じて、適切なアクションを実行します。 これを実行する方法を次のコード例に示します。  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これらの例には次の項目が必要です。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  また、「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
