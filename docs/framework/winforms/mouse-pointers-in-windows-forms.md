---
title: Windows フォームにおけるマウス ポインター
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: ed6312cb386d1557d4217a330318664b4e87c330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539518"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows フォームにおけるマウス ポインター
マウス*ポインター*マウスを使用してユーザー入力を画面のフォーカス ポイントを指定するビットマップは、そのカーソルと呼ばします。 このトピックでは、Windows フォームにおけるマウス ポインターの概要を説明し、変更およびマウス ポインターを制御する方法をいくつかについて説明します。  
  
## <a name="accessing-the-mouse-pointer"></a>マウス ポインターへのアクセス  
 マウス ポインターがによって表される、<xref:System.Windows.Forms.Cursor>クラス、および各<xref:System.Windows.Forms.Control>が、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>そのコントロールのポインターを指定するプロパティです。 <xref:System.Windows.Forms.Cursor>クラスにはなど、ポインターを記述するプロパティが含まれています、<xref:System.Windows.Forms.Cursor.Position%2A>と<xref:System.Windows.Forms.Cursor.HotSpot%2A>プロパティ、およびメソッドなど、ポインターの外観を変更できる、 <xref:System.Windows.Forms.Cursor.Show%2A>、 <xref:System.Windows.Forms.Cursor.Hide%2A>、および<xref:System.Windows.Forms.Cursor.DrawStretched%2A>メソッド。  
  
## <a name="controlling-the-mouse-pointer"></a>マウス ポインターを制御します。  
 マウス ポインターが使用できるまたはマウスの位置を変更する領域を制限する場合があります。 取得またはマウスを使用して、現在の場所を設定することができます、<xref:System.Windows.Forms.Cursor.Position%2A>のプロパティ、<xref:System.Windows.Forms.Cursor>です。 マウス ポインターを使用できる領域を制限するさらに、設定は、<xref:System.Windows.Forms.Cursor.Clip%2A>プロパティです。 クリップ領域で、既定では、画面全体です。  
  
## <a name="changing-the-mouse-pointer"></a>マウス ポインターを変更します。  
 マウス ポインターを変更するは、ユーザーにフィードバックを提供することの重要な方法です。 ハンドラーでマウス ポインターを変更するなど、<xref:System.Windows.Forms.Control.MouseEnter>と<xref:System.Windows.Forms.Control.MouseLeave>計算が行われていることをユーザーに伝えるためと、コントロール内のユーザーの操作を制限するイベントです。 場合によっては、マウス ポインターがドラッグ アンド ドロップ操作で、アプリケーションが関係している場合など、システム イベントによって変更されます。  
  
 マウス ポインターを変更する主な方法は、設定して、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.Control.DefaultCursor%2A>を新しいコントロールのプロパティの<xref:System.Windows.Forms.Cursor>します。 マウス ポインターを変更する例のコード例を参照してください、<xref:System.Windows.Forms.Cursor>クラスです。 さらに、<xref:System.Windows.Forms.Cursors>クラスのセットを公開する<xref:System.Windows.Forms.Cursor>ポインター、手の形のようなポインターなどのさまざまな種類のオブジェクト。 砂時計が、コントロールにマウス ポインターがあるたびに似ていますが、待機のポインターを表示するには、<xref:System.Windows.Forms.Control.UseWaitCursor%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Cursor>  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows フォームにおけるドラッグ アンド ドロップ機能](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
