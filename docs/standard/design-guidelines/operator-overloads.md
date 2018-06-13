---
title: 演算子のオーバーロード
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 747fc21aceae60e362c72391ae265e45d6f8445f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579315"
---
# <a name="operator-overloads"></a>演算子のオーバーロード
演算子のオーバー ロードは、framework の型をした組み込みの言語プリミティブを表示を許可します。  
  
 許可されている、いくつかの状況で役に立ちますが、演算子のオーバー ロードを慎重に使用してください。 演算子のオーバー ロードがされて悪用などの単純なメソッドにする必要のある操作で演算子を使用するフレームワークの設計者が開始されたときに多くの場合があります。 次のガイドラインには、演算子のオーバー ロードを使用するタイミングと方法を決定するのに役立ちます。  
  
 **避け x**を除く演算子のオーバー ロードを定義する必要があります (組み込み) のプリミティブ型と感じての種類でします。  
  
 **✓ を検討してください**演算子のオーバー ロードを定義する型がプリミティブ型のように感じる必要があります。  
  
 たとえば、<xref:System.String?displayProperty=nameWithType>が`operator==`と`operator!=`定義します。  
  
 **✓ しないで**番号を表す構造体で演算子オーバー ロードを定義する (など<xref:System.Decimal?displayProperty=nameWithType>)。  
  
 **X しないで**演算子のオーバー ロードを定義するときに分別して使用します。  
  
 演算子のオーバー ロードが簡単にすぐに操作の結果がどうなる場合に便利です。 1 を減算できる理にかなってなど<xref:System.DateTime>別の`DateTime`を取得し、<xref:System.TimeSpan>です。 ただしが適切でない共用体の 2 つのデータベース クエリでは、論理、union 演算子を使用するか、ストリームに書き込むシフト演算子を使用します。  
  
 **X しないで**オーバー ロードを定義する型のオペランドの少なくとも 1 つがない限り、演算子がオーバー ロードを提供します。  
  
 **✓ しないで**対称的に演算子をオーバー ロードします。  
  
 たとえば、オーバー ロードする場合、`operator==`もオーバー ロードする必要がある、`operator!=`です。 同様に、オーバー ロードする場合、`operator<`もオーバー ロードする必要がある、`operator>`のようにします。  
  
 **✓ を検討してください**各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを提供します。  
  
 多くの言語は、演算子のオーバー ロードをサポートしていません。 このため、演算子をオーバー ロードする型が、同等の機能は、適切なドメイン固有の名前を持つセカンダリ メソッドを含めることをお勧めします。  
  
 次の表には、演算子と、対応するわかりやすいメソッド名の一覧が含まれています。  
  
|C# 演算子記号|メタデータ名|フレンドリ名|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a>演算子をオーバー ロード = =  
 オーバー ロード`operator ==`はかなり複雑になります。 演算子のセマンティクスをなどの他のいくつかのメンバーと互換性がある必要があります<xref:System.Object.Equals%2A?displayProperty=nameWithType>です。  
  
### <a name="conversion-operators"></a>変換演算子  
 変換演算子は、単項演算子を別の型に変換できるようにします。 演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。 変換演算子の 2 種類があります。 明示的および暗黙的なです。  
  
 **X しないで**エンドユーザーでこのような変換が明確に予期されていない場合は、変換演算子を提供します。  
  
 **X しないで**型のドメインの外部の変換演算子を定義します。  
  
 たとえば、 <xref:System.Int32>、 <xref:System.Double>、および<xref:System.Decimal>はのすべての数値型に対し<xref:System.DateTime>はありません。 したがって、存在しないはず変換演算子に変換する、`Double(long)`を`DateTime`です。 コンス トラクターは、このような場合が優先されます。  
  
 **X しないで**変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。  
  
 たとえば、存在することはできませんから暗黙的な変換`Double`に`Int32`ため`Double`よりも広い範囲を持つ`Int32`します。 変換が損失を伴う可能性がある場合でも、明示的な変換演算子を指定することができます。  
  
 **X しないで**暗黙的なキャストから例外をスローします。  
  
 エンドユーザーがないかもしれません変換が行われているために、何が起こっているかを理解するため非常に困難です。  
  
 **✓ しないで**スロー<xref:System.InvalidCastException?displayProperty=nameWithType>でキャスト演算子への呼び出しが損失を伴う変換と演算子のコントラクトでは、非可逆の変換は許可されません。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
