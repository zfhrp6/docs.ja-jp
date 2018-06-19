---
title: クラスまたは構造体の選択
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bb05b825113c025781a790dc206d500633a3b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573582"
---
# <a name="choosing-between-class-and-struct"></a>クラスまたは構造体の選択
すべての framework デザイナーに直面して基本的な設計上の決定の 1 つは、クラス (参照型)、または構造体 (値型) として型をデザインするかどうかです。 参照型と値の型の動作の違いをよく理解は、このオプションを選択する際に非常に重要です。  
  
 最初の間に違いが参照型と値の型を検討します。 はある参照型と、ガベージ コレクション ヒープに割り当てられている値の型が割り当てられたスタックのいずれかまたはインラインでを含む型し割り当て解除されたときに対し、スタックアンワインドを取得、含んでいる型の割り当てを解除する場合またはします。 したがって、値型の割り当てと解放は一般に参照型の割り当てと解放より低コストです。  
  
 次に、参照型の配列ではの不一致、つまり、配列要素に、ヒープ上に存在する参照型のインスタンスへの単なる参照が割り当てられます。 値型の配列には、インライン、つまり、配列要素値の型の実際のインスタンスが割り当てられます。 そのため、値型の配列の割り当てと解放は、参照型の配列の割り当てと解放よりはるかに安いです。 さらに、多くの場合は、値型の配列と、参照の局所性量が高くが発生します。  
  
 次の相違点については、メモリ使用量に関連します。 値型は、参照型または実装するインターフェイスの 1 つにキャストするときをボックス化を取得します。 ボックス化解除された取得した値の型にキャストされる場合。 ボックスは、ヒープで割り当てられるし、は、ガベージ コレクション、あまりボックス化およびボックス化解除されるオブジェクトであるため、ヒープ、ガベージ コレクターと最終的には、アプリケーションのパフォーマンスに悪影響を与えることができます。  これに対し、このようなボックス化は行われませんように参照型にキャストされます。  
  
 次に、参照型の割り当ては、値型の割り当て値全体をコピーする一方、参照をコピーします。 したがって、大規模な参照型の割り当ては、大きな値の型の割り当てよりも安価です。  
  
 最後に、値の型が値によって渡されるが、参照型は、参照によって渡されます。 参照型のインスタンスへの変更では、インスタンスを指すすべての参照に影響します。 値型のインスタンスは、値によって渡されるときにコピーされます。 値型のインスタンスが変更されたときに、もちろんには影響しません、そのコピーのいずれか。 コピーは、ユーザーによって明示的に作成されませんが、引数が渡されるまたは返される値を返すときに暗黙的に作成された、変更可能な値の型が多数のユーザーに混乱する可能性です。 そのため、値の型は変更できません。  
  
 原則として、として、framework の型の大部分は、クラスをする必要があります。 ただし、状況によっては、値型の特性ように構造体を使用する適切ながあります。  
  
 **✓ を検討してください**型のインスタンスは小さく、一般的な有効期間が短いまたはその他のオブジェクトに埋め込まれている一般的な場合は、クラスの代わりに構造体を定義することです。  
  
 **避け x**すべて次の特徴の種類があるない限り、構造体を定義します。  
  
-   プリミティブ型のような単一の値を論理的に表す (`int`、 `double`, などです。)。  
  
-   16 バイト未満のサイズのインスタンスがあります。  
  
-   変更可能なことはできません。  
  
-   頻繁にボックス化することはありません。  
  
 その他のすべてのケースでクラスとして、型を定義する必要があります。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
