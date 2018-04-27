---
title: パラメーターに名前を付ける
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e5dfe35fd4f2939898acee44764535c6de5fe9e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="naming-parameters"></a>パラメーターに名前を付ける
読みやすくするための明確な理由から、以外には、パラメーターは、ドキュメントでは、デザイナーで表示されるビジュアル デ ザイン ツール Intellisense および参照機能クラスを指定するときにためパラメーターの名前に関するガイドラインに従う必要があります。  
  
 **✓ しないで**パラメーター名の camel 表記を使用します。  
  
 **✓ しないで**わかりやすいパラメーター名を使用します。  
  
 **✓ を検討してください**パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。  
  
### <a name="naming-operator-overload-parameters"></a>演算子のオーバー ロードのパラメーターの名前を付ける  
 **✓ は**使用`left`と`right`のパラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。  
  
 **✓ しないで**使用`value`で単項演算子のオーバー ロード パラメーター名はパラメーターに意味がない場合。  
  
 **✓ を検討してください**演算子にわかりやすい名前オーバー ロードのパラメーターの場合は重要な価値が追加されます。  
  
 **X しないで**使用の省略形または数値の添字演算子のオーバー ロードのパラメーターの名前。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
