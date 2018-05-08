---
title: リソースに名前を付ける
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7cfda4e6a340d040de02903b9b64f0339751c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="naming-resources"></a>リソースに名前を付ける
ローカライズ可能なリソースは、これらのプロパティの場合と同様、特定のオブジェクトから参照できる、ために、リソースの名前付けのガイドラインは、プロパティのガイドラインに似ています。  
  
 **✓ しないで**リソース キーで pascal 表記を使用を使用します。  
  
 **✓ しないで**短い識別子ではなくわかりやすいを提供します。  
  
 **X しないで**メインの CLR 言語の言語固有のキーワードを使用します。  
  
 **✓ しないで**のみ英数字とアンダー スコアを使用してリソースの名前付けで使用します。  
  
 **✓ しないで**例外メッセージのリソースに対して次の命名規則を使用します。  
  
 リソース識別子は、例外の種類名と、例外の短い識別子にする必要があります。  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
