---
title: "SplitContainer コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SplitContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SplitContainer コントロール [Windows フォーム], SplitContainer コントロールの概要"
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# SplitContainer コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.SplitContainer> コントロールは、移動できるバーによって分割された 2 つのパネルから成る複合コントロールと考えることができます。  マウス ポインターをバーの上に置くと、ポインターが変形し、そのバーを移動できることが示されます。  
  
> [!IMPORTANT]
>  **ツールボックス**では、以前のバージョンの [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] で使用されていた <xref:System.Windows.Forms.Splitter> コントロールが、<xref:System.Windows.Forms.SplitContainer> コントロールに置き換えられました。  <xref:System.Windows.Forms.SplitContainer> コントロールの優先度は、<xref:System.Windows.Forms.Splitter> コントロールよりもかなり高くなります。  <xref:System.Windows.Forms.Splitter> クラスは、既存のアプリケーションとの互換性を確保するために、引き続き [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] に含まれていますが、新しいプロジェクトに対しては、<xref:System.Windows.Forms.SplitContainer> コントロールを使用することを強くお勧めします。  
  
 <xref:System.Windows.Forms.SplitContainer> コントロールを使用すると、複雑なユーザー インターフェイスを作成できます。多くの場合、1 つのパネルで選択した項目によって、他のパネルで表示されるオブジェクトが決まります。  この配置は、情報の表示と参照には非常に有効です。  2 つのパネルを用意することで、領域に情報を集約でき、さらに、バーまたは "分割線" により、ユーザーが簡単にパネルのサイズを変更できます。  
  
 第 2 の <xref:System.Windows.Forms.SplitContainer> コントロールを水平方向に配置した状態で、複数の <xref:System.Windows.Forms.SplitContainer> コントロールを入れ子にして、上部のパネルと下部のパネルを作成することもできます。  
  
 既定では、<xref:System.Windows.Forms.SplitContainer> コントロールにはキーボードからアクセスできます。<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティが `false` に設定されていれば、ユーザーは方向キーを押して分割線を移動できます。  
  
 <xref:System.Windows.Forms.SplitContainer> コントロールの <xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティは、コントロール自体の方向ではなく、分割線の方向を指定します。  そのため、このプロパティが <xref:System.Windows.Forms.Orientation> に設定されているときは、上から下に向かって分割線が作成され、左パネルと右パネルが作成されます。  
  
 また、<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> プロパティの値は、<xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティの値に応じて決定されることに注意してください。  詳細については、「<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> プロパティ」を参照してください。  
  
 <xref:System.Windows.Forms.SplitContainer> コントロールのサイズと移動を制限することもできます。  <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> プロパティでは、<xref:System.Windows.Forms.SplitContainer> コントロールのサイズを変更した後に同じサイズのままで維持するパネルが決定され、<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティでは、分割線がキーボードまたはマウスによって移動できるかどうかが決定されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティが `true` に設定されている場合でも、<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティを使用するなどの方法で、プログラムによって分割線を移動させることができます。  
  
 最後に、<xref:System.Windows.Forms.SplitContainer> コントロールの各パネルには、個々のサイズを決定するプロパティが用意されています。  
  
## 一般的に使用されるプロパティ、メソッド、およびイベント  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> プロパティ|<xref:System.Windows.Forms.SplitContainer> コントロールのサイズを変更した後に同じサイズのままで維持するパネルを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ|分割線がキーボードまたはマウスによって移動できるかどうかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティ|分割線を垂直方向と水平方法のどちらで配置するかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ|左端または上端から移動できる分割バーまでの距離 \(ピクセル単位\) を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ|ユーザーが分割線を移動できる最小距離 \(ピクセル単位\) を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> プロパティ|分割線の幅 \(ピクセル単位\) を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> イベント|分割線の移動中に発生します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> イベント|分割線の移動後に発生します。|  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [SplitContainer Control Sample](http://msdn.microsoft.com/ja-jp/9015fad0-7108-4d85-a83a-a72d038c4f65)