---
title: "Splitter コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "Splitter"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Splitter コントロール [Windows フォーム], Splitter コントロールの概要"
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Splitter コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.SplitContainer> コントロールは、以前のバージョンの <xref:System.Windows.Forms.Splitter> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.Splitter> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォームの <xref:System.Windows.Forms.Splitter> コントロールを使用すると、ドッキングされたコントロールのサイズを実行時に変更できます。  通常、<xref:System.Windows.Forms.Splitter> コントロールは、さまざまな長さのデータが表示されるコントロールのあるフォーム上で使用します。たとえば、エクスプローラーのデータ ペインには、状況に応じて異なる幅の情報が含まれています。  
  
## Splitter コントロールの操作  
 Splitter コントロールによってサイズ変更できるコントロール内で、ドッキングされていない端にユーザーがマウス ポインターを置くと、ポインターが変形し、このコントロールのサイズを変更できることが示されます。  Splitter コントロールを使用すると、そのすぐ前にあるドッキングされたコントロールをユーザーがサイズ変更できるようになります。  このため、ドッキングされたコントロールのサイズを実行時にユーザーが変更できるようにするには、サイズ変更するコントロールをコンテナーの端にドッキングしてから、コンテナーの同じ側に Splitter コントロールをドッキングする必要があります。  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [方法 : Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)