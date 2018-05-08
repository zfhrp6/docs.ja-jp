---
title: グラフィックス コンテナーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: 8755a95434d3fed06a55cfca0f71d86e5521cb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-graphics-containers"></a>グラフィックス コンテナーの使用
A<xref:System.Drawing.Graphics>オブジェクトなどのメソッドを提供<xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawImage%2A>、および<xref:System.Drawing.Graphics.DrawString%2A>ベクター イメージ、ラスター イメージおよびテキストを表示するためです。 A<xref:System.Drawing.Graphics>オブジェクトに品質と印刷の向きに描画される項目の影響を与えるいくつかのプロパティもあります。 たとえば、スムージング モード プロパティは、直線と曲線にアンチエイリアシングを適用し、位置と回転に描画される項目のワールド変換プロパティに影響を与えますかどうかを判断します。  
  
 A<xref:System.Drawing.Graphics>オブジェクトが特定のディスプレイ デバイスに関連付けられます。 使用する場合、<xref:System.Drawing.Graphics>のウィンドウで描画するオブジェクト、<xref:System.Drawing.Graphics>オブジェクトは、その特定の期間に関連付けられてもいます。  
  
 A<xref:System.Drawing.Graphics>オブジェクトはコンテナーとして描画に影響を与えるプロパティのセットが格納されているためと、デバイスに固有の情報にリンクされています。 内で、既存のセカンダリのコンテナーを作成できます<xref:System.Drawing.Graphics>オブジェクトを呼び出して、<xref:System.Drawing.Graphics.BeginContainer%2A>そのメソッド<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Graphics オブジェクトの状態の管理](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 について説明します、品質の設定、クリッピング領域との変換の管理方法、<xref:System.Drawing.Graphics>オブジェクト。  
  
 [入れ子になっているグラフィックス コンテナーの使用](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 コンテナーの状態の制御を使用する方法を示します、<xref:System.Drawing.Graphics>オブジェクト。
