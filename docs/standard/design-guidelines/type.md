---
title: 型のデザインのガイドライン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af7511f4159fdbfe2d3f972dc927e9ee11fd586f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572890"
---
# <a name="type-design-guidelines"></a>型のデザインのガイドライン
CLR の観点からは、型の 2 つのカテゴリがあります: 参照型と値の型: フレームワーク デザインの詳細については、するためにお種類以上の論理グループ分け、それぞれ独自の特定のデザイン規則には。  
  
 クラスは、参照型の一般的なケースです。 ほとんどのフレームワークの型の大部分を構成します。 クラスは、豊富なサポートされるオブジェクト指向の機能の設定と、一般的な適用性、人気を支払わなかったです。 基本クラスと抽象クラスは、拡張機能に関連する特殊な論理グループです。  
  
 インターフェイスは、参照型と値の型の両方によって実装可能な型の型です。 したがって、参照型と値の型のポリモーフィックな階層のルートとして使用することができます。 さらに、インターフェイスを使用して、CLR によってネイティブにサポートされていない複数の継承をシミュレートすることができます。  
  
 構造体は、値型の一般的なケースがあり、小規模で単純な種類、言語プリミティブのような用に予約する必要があります。  
  
 列挙型は、日、週、コンソールの色、およびなどのような値の短いセットを定義するために使用する値型の特殊なケースです。  
  
 静的クラスは、静的メンバーのコンテナーを目的としての種類です。 その他の操作へのショートカットを提供するよく使用されます。  
  
 デリゲート、例外、属性、配列、およびコレクションは、特別な用途のためのもので、参照型のすべての特殊なケースであり、設計と使用法についてのガイドラインがこのドキュメントで部分で説明されています。  
  
 **✓ しないで**各型が適切に定義された一連の関連するメンバーは、関連付けられていない機能のランダムなコレクションだけでなくであることを確認します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象クラスのデザイン](../../../docs/standard/design-guidelines/abstract-class.md)  
 [静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)  
 [インターフェイスのデザイン](../../../docs/standard/design-guidelines/interface.md)  
 [構造体のデザイン](../../../docs/standard/design-guidelines/struct.md)  
 [列挙型デザイン](../../../docs/standard/design-guidelines/enum.md)  
 [入れ子にされた型](../../../docs/standard/design-guidelines/nested-types.md)  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
