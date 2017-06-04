---
title: "ダブル バッファリングの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "バッファリング, ダブル バッファリング"
  - "ダブル バッファリング"
  - "ちらつき, 低減 (Windows フォーム内の)"
  - "グラフィックス, ダブル バッファリング"
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# ダブル バッファリングの使用
グラフィックスにダブル バッファリングを使用すると、複雑な描画操作を必要とするアプリケーションでちらつきを抑えることができます。  .NET Framework にはダブル バッファリングのサポートが組み込まれています。または、グラフィックスを手動で管理して描画することも可能です。  
  
## このセクションの内容  
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 ダブル バッファリングの概要を紹介し、.NET Framework によるサポートについて大まかに説明します。  
  
 [方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 .NET Framework でサポートされる既定のダブル バッファリングの使用方法について説明します。  
  
 [方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 アプリケーションでダブル バッファリングを管理する方法について説明します。  
  
 [方法 : バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 ダブル バッファリングを使用してグラフィックスを描画する方法について説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 ダブル バッファリングを可能にするメソッドを制御します。  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 グラフィックスのバッファーを作成するメソッドを提供します。  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 バッファーに格納されたグラフィックス コンテキストへのアクセスをアプリケーション ドメインに提供します。