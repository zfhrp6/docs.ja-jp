---
title: "SplitContainer コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d2e538241cca8288158628df777895fae9aa756
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.SplitContainer> コントロールは複合と考えることができ、移動可能なバーで区切られた 2 つのパネルです。 マウス ポインターがバーの上に移動すると、ポインターの形が変わり、バーが移動可能であることを示します。  
  
> [!IMPORTANT]
>  **ツールボックス**、<xref:System.Windows.Forms.SplitContainer>置換の制御、<xref:System.Windows.Forms.Splitter>の以前のバージョンに存在していたコントロール[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。 <xref:System.Windows.Forms.SplitContainer> コントロールは <xref:System.Windows.Forms.Splitter> コントロールより優先されます。 <xref:System.Windows.Forms.Splitter>クラスは可能です、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 、既存のアプリケーションとの互換性を強くお勧めを使用することが、<xref:System.Windows.Forms.SplitContainer>新しいプロジェクトのコントロールです。  
  
 <xref:System.Windows.Forms.SplitContainer>コントロール、複雑なユーザー インターフェイスを作成することができます。 多くの場合、1 つのパネルで選択した項目によって、もう一方のパネルにどのようなオブジェクトが表示されます。 この配置は、情報の表示と参照に対して非常に効果的です。 2 つのパネルで地域では、情報を集計して、バー、または「分割」により、パネルのサイズを変更するユーザーの簡単です。  
  
 1 つ以上<xref:System.Windows.Forms.SplitContainer>コントロール ネストすることも、2 番目の<xref:System.Windows.Forms.SplitContainer>コントロール指向の水平方向には、上部と下部のパネルを作成します。  
  
 注意してくださいを<xref:System.Windows.Forms.SplitContainer>コントロールがキーボードからアクセス可能な既定以外のユーザーが分割線の移動方向キーを押すことができます、<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティに設定されている`false`です。  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A>のプロパティ、<xref:System.Windows.Forms.SplitContainer>コントロールは、スプリッターのではなく、コントロール自体の方向を決定します。 そのため、このプロパティ設定されている場合<xref:System.Windows.Forms.Orientation.Vertical>、分割線を上から下、左と右のパネルを作成する実行します。  
  
 またの値、<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>プロパティの値によって異なります、<xref:System.Windows.Forms.SplitContainer.Orientation%2A>プロパティです。 詳細については、次を参照してください。<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>プロパティです。  
  
 移動とサイズを制限することも、<xref:System.Windows.Forms.SplitContainer>コントロール。 <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>プロパティを決定するパネルが後に同じサイズのまま、<xref:System.Windows.Forms.SplitContainer>コントロールのサイズが、および<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティは、スプリッターは、キーボードまたはマウスを移動できるかどうかを決定します。  
  
> [!NOTE]
>  場合でも、<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティに設定されている`true`、分割線も移動を許可するプログラム。 たとえば、を使用して、<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>プロパティです。  
  
 最後に、各パネル、<xref:System.Windows.Forms.SplitContainer>コントロール、個々 のサイズを決定するプロパティがあります。  
  
## <a name="commonly-used-properties-methods-and-events"></a>一般的に使用されるプロパティ、メソッド、およびイベント  
  
|name|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> プロパティ|どのパネルは変わりませんを決定後サイズ、<xref:System.Windows.Forms.SplitContainer>コントロールのサイズを変更します。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ|キーボードまたはマウスで分割線を移動できるかどうかを判断します。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティ|分割線が垂直または水平方向に配置されているかどうかを判断します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ|移動可能な分割バーを左端または上端からのピクセル単位で距離を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ|最小の距離 (ピクセル単位)、スプリッターをユーザーが移動できることを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> プロパティ|分割線のピクセル単位の太さを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> イベント|分割境界線が移動するときに発生します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> イベント|分割境界線が移動されたときに発生します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [SplitContainer コントロールのサンプル](http://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
