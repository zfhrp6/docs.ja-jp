---
title: "シールされていないクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a>シールされていないクラス
シール クラスは継承できませんし、機能拡張するを防ぎます。 これに対し、封印されていないクラスから継承できるクラスと呼びます。  
  
 **✓ を検討してください**安価なを提供するのにまだ高く評価されたフレームワークを拡張機能として、仮想またはプロテクト メンバーを追加なしで封印されていないクラスを使用します。  
  
 多くの場合、開発者はカスタム コンス トラクター、新しいメソッド、またはメソッドのオーバー ロードなどの便利なメンバーを追加するために、封印されていないクラスから継承したいと考えているとします。 たとえば、`System.Messaging.MessageQueue`が封印されていないとできるので、ユーザーのキューを作成するカスタムな特定のキューのパスにその既定値または特定のシナリオ用の API を簡略化するカスタム メソッドを追加します。  
  
 既定ではほとんどのプログラミング言語でクラスが封印されていないし、これも推奨される既定のフレームワークのほとんどのクラス。 Unsealed 型によって提供される機能拡張は、フレームワークのユーザーがかなり歓迎いたし、unsealed 型に関連付けられているテストの比較的低コストのために提供する非常に低コストです。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のための設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [封印](../../../docs/standard/design-guidelines/sealing.md)
