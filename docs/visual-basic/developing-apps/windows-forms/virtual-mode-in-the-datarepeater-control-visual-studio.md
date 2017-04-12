---
title: "DataRepeater コントロール (Visual Studio) での仮想モード |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 85f7e250c57a507e891eb30756c0550098cce9e0
ms.lasthandoff: 03/13/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater コントロールの仮想モード (Visual Studio)
大量の表形式データを表示する場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを設定してパフォーマンスを向上させることができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`と明示的にそのデータ ソース コントロールの相互作用を管理します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールには、データ ソースとやり取りし、実行時に、必要に応じて、データを表示するために利用できるいくつかのイベントが用意されています</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
## <a name="how-virtual-mode-works"></a>仮想モードの動作  
 最も一般的なシナリオ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、コントロールの子コントロールをバインドする、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>データにでき、デザイン時にソース、<xref:System.Windows.Forms.BindingSource>必要に応じて、双方向にデータを渡す</xref:System.Windows.Forms.BindingSource></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 仮想モードを使用して、コントロールがデータ ソースにバインドされていないデータがやり取りされる基になるデータ ソースに実行時にします。  
  
 ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>にプロパティが設定されている`True`からコントロールを追加して、ユーザー インターフェイスを作成する、**ツールボックス**からバインドされたコントロールを追加する代わりに、**データソース**ウィンドウ</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>。  
  
 コントロールごとにイベントが発生して、データの表示を処理するコードを追加する必要があります。 新しい<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>がビューにスクロールされる基準、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベントの各コントロールの&1; つの時間が発生し、内の各コントロールの値を指定する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベント ハンドラー</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 。  
  
 コントロールのいずれかでデータが、ユーザーが変更された場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>イベントが発生し、データを検証し、データ ソースに保存する必要があります</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>。  
  
 ユーザーが新しい項目を追加する場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>イベントが発生します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>。 このイベントのハンドラーを使用して、データ ソースに新しいレコードを作成します。 意図しない変更を防ぐためには、監視する必要も、<xref:System.Windows.Forms.Control.KeyDown>の各コントロールと呼び出しイベント<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>場合は、ユーザーが ESC キーを押した</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A></xref:System.Windows.Forms.Control.KeyDown>。  
  
 データ ソースが変更する場合は、更新、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを呼び出して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>メソッド</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 順序では、両方のメソッドを呼び出す必要があります。  
  
 最後に、イベント ハンドラーを実装する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>の直接的および必要に応じて項目が削除されるときに発生するイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>イベントでは、ユーザーが DELETE キーを押すと項目を削除するたびに発生します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>。  
  
## <a name="implementing-virtual-mode"></a>仮想モードの実装  
 仮想モードを実装するために必要な手順を次に示します。  
  
#### <a name="to-implement-virtual-mode"></a>仮想モードを実装するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールから、 **Visual Basic power Packs**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>。  
  
2.  コントロールをドラッグ、**ツールボックス**の項目テンプレートの領域 (上の領域) に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 1 つのコントロールは、各フィールドを表示する、データ ソース内の必要があります。  
  
3.  ハンドラーを実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>イベントの各コントロールの値を指定します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>。 このイベントは、新しい<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>スクロールして表示します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。 コードはという名前のデータ ソースの場合は次の例のように`Employees`します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  ハンドラーを実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>データを格納するイベントです</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>。 このイベントは、ユーザーが<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>の子コントロールに変更をコミットと発生します。 コードはという名前のデータ ソースの場合は次の例のように`Employees`します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  子コントロールごとにハンドラーを実装<xref:System.Windows.Forms.Control.KeyDown>イベントと、ESC キーを監視します</xref:System.Windows.Forms.Control.KeyDown>。 呼び出す、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>しないようにする方法、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>イベントの発生します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>。 コードは、次の例ようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  ハンドラーを実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>イベント</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>。 このイベントは、ユーザーが新しいアイテムを追加すると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 コードはという名前のデータ ソースの場合は次の例のように`Employees`します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  ハンドラーを実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>イベント</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>。 このイベントは、ユーザーが既存の項目を削除したときに発生します。 コードはという名前のデータ ソースの場合は次の例のように`Employees`します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  ハンドラーを必要に応じてコントロール レベルの検証の実装、<xref:System.Windows.Forms.Control.Validating>子コントロールのイベント</xref:System.Windows.Forms.Control.Validating>。 コードは、次の例ようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
