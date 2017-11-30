---
title: "ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ
Windows フォームの標準的なツールボックス上のコントロールは、キーボード フォーカスを公開することや、画面要素を公開するなど、ユーザー補助ガイドラインの多くをサポートします。  
  
## <a name="planning-ahead-for-accessibility"></a>ユーザー補助の事前の計画  
 コントロールのプロパティは、次の表に示すように、その他のユーザー補助ガイドラインをサポートするために使用できます。 さらに、プログラムの機能へのアクセスを提供するのにメニューを使用する必要があります。  
  
|コントロールのプロパティ|ユーザー補助機能に関する考慮事項|  
|----------------------|--------------------------------------|  
|AccessibleDescription|説明については、スクリーン リーダーなどのユーザー補助機能に報告されます。 ユーザー補助機能は専用のプログラムおよびデバイスで、障碍を持つユーザーがコンピューターをより効果的に使用するよう助けます。|  
|AccessibleName|ユーザー補助機能に報告される名前です。|  
|AccessibleRole|ユーザー インターフェイスの要素の使用方法をについて説明します。|  
|TabIndex|フォームで実用的な移動パスを作成します。 など、関連するラベルのタブ オーダーの直前に、テキスト ボックスに、固有のラベルを持たないコントロールの重要です。|  
|テキスト|"&"の文字を使用して、アクセス キーを作成します。 アクセス キーの使用は、機能を文書化されたキーボード アクセスを提供する部分です。|  
|フォント サイズ|フォント サイズが調整可能でない場合は、10 ポイント以上に設定する必要があります。 フォームのフォント サイズを設定すると、後からフォームに追加されるすべてのコントロールが同じサイズになります。|  
|前景色|このプロパティが既定値に設定されている場合、フォームにユーザーのカラー設定が使用されます。|  
|背景色|このプロパティが既定値に設定されている場合、フォームにユーザーのカラー設定が使用されます。|  
|BackgroundImage|このプロパティは、テキストを読みやすくする場合は空白のままにします。|  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ユーザー補助対応の Windows ベースのアプリケーションの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
