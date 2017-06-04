---
title: "Using Manipulations and Inertia in an XNA Application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Using Manipulations and Inertia in an XNA Application
この記事では、操作と慣性の処理を Microsoft XNA アプリケーションで使用して、ゲーム ピースの動きを制御する方法について説明します。  この記事をお読みになる前に、「[Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)」トピックの内容、および基本的な XNA のプログラミングの概念についてよく理解してください。  
  
 この記事で説明するタスクを実行するには、XNA プロジェクトが <xref:System.Windows.Input.Manipulations> アセンブリを参照しているとともに、[XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) \([ダウンロード](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)\) がコンピューターにインストールされて、プロジェクトが XNA アセンブリを参照できる状態になっている必要があります。  
  
## 機能の概要  
 この記事では、操作と慣性の処理を使用するゲーム ピースを表すカスタム クラスの作成方法を示します。  このクラスを使用すると、マウスでゲーム ピースをドラッグしてから放すことで、画面全体で操作できるようになります。  ゲーム ピースを放すと、慣性の処理により、ゲーム ピースの移動速度が徐々に低下します。  直線運動と角運動の両方が行われます。  
  
 ![単純な操作と慣性のアプリケーション](../../../docs/framework/common-client-technologies/media/ndp-gamexna.png "NDP\_GameXna")  
  
 さらに、複数のゲーム ピースを管理するカスタム コレクションが作成されます。  これにより、XNA Game クラスから必要とされる処理が簡略化します。  
  
 [Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Full Code Listings](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## 参照  
 <xref:System.Windows.Input.Manipulations>   
 [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)