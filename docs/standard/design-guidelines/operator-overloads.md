---
title: "演算子のオーバー ロード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "[.NET Framework] ダイアログ ボックスの演算子のオーバー ロード"
  - "名前 [.NET Framework] のオーバー ロードされた演算子"
  - "メンバー デザインのガイドライン, オペレーター"
  - "オーバーロードされた演算子"
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 演算子のオーバー ロード
演算子のオーバー ロードでは、組み込みの言語プリミティブに存在した場合のように表示されるフレームワークの種類を許可します。  
  
 許可されている、いくつかの状況で便利ですが、慎重に行って演算子のオーバー ロードを使用してください。 演算子のオーバー ロードがされて悪用の簡単な方法があります。 操作に演算子を使用するフレームワークの設計者の起動時など、多くの場合があります。 次のガイドラインは、演算子のオーバー ロードを使用するタイミングと方法を決定するのに役立ちます。  
  
 **X 回避** を除くいえますプリミティブ \(組み込み\) 型のような種類の演算子のオーバー ロードを定義します。  
  
 **✓ を検討してください** プリミティブ型のように感じがする型の演算子のオーバー ロードを定義します。  
  
 たとえば、 <xref:System.String?displayProperty=fullName> が `operator==` と `operator!=` を定義します。  
  
 **✓ は** 演算子のオーバー ロードを数値を表現する構造体の定義 \(など <xref:System.Decimal?displayProperty=fullName>\)。  
  
 **X のしないで** 演算子のオーバー ロードを定義するときに、利かせようです。  
  
 演算子のオーバー ロードは、順番を一見して、操作の結果はどのくらいにする場合に便利です。 合理的に 1 を減算するたとえば、 <xref:System.DateTime> 別の `DateTime` を取得し、 <xref:System.TimeSpan>です。 ただし、共用体の 2 つのデータベース クエリに論理演算子を使用するか、ストリームに書き込むシフト演算子を使用する適切ではありません。  
  
 **X のしないで** オーバー ロードを定義する型のオペランドの少なくとも 1 つがない場合、演算子がオーバー ロードを提供します。  
  
 **✓ は** 演算子は対称的にオーバー ロードします。  
  
 たとえば、オーバー ロードする場合、 `operator==`, 、オーバー ロードもする必要があります、 `operator!=`です。 同様に、オーバー ロードする場合、 `operator<`, 、オーバー ロードする必要がありますも、 `operator>`, 、という具合です。  
  
 **✓ を検討してください** 各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを指定します。  
  
 多くの言語は、演算子のオーバー ロードをサポートしていません。 このため、演算子をオーバー ロードする型が同等の機能は、適切なドメイン固有の名前を持つセカンダリ メソッドを含めることをお勧めします。  
  
 次の表には、演算子と対応するわかりやすいメソッド名の一覧が含まれています。  
  
|C\# 演算子シンボル|メタデータ名|フレンドリ名|  
|-----------------|------------|------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|`&#124;`|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|`&#124;&#124;`|`op_LogicalOr`|`Or`|  
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
|`&#124;=`|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### 演算子をオーバー ロード \= \=  
 オーバー ロード `operator ==` はかなり複雑になります。 演算子のセマンティクスをなどその他のいくつかのメンバーと互換性がある必要がある <xref:System.Object.Equals%2A?displayProperty=fullName>です。  
  
### 変換演算子  
 変換演算子は、単項演算子を別の型に変換できるようにします。 演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。 変換演算子の 2 種類があります。 明示的および暗黙的なです。  
  
 **X のしないで** 場合は、エンドユーザーがこのような変換が明確に予期しない変換演算子が用意されています。  
  
 **X のしないで** 型のドメインの外部での変換演算子を定義します。  
  
 たとえば、 <xref:System.Int32>, 、<xref:System.Double>, 、および <xref:System.Decimal> はすべての数値型に対し <xref:System.DateTime> はありません。 そのためがあってはなりません変換への変換演算子、 `Double(long)` に、 `DateTime`です。 コンス トラクターは、このような場合が優先されます。  
  
 **X のしないで** 変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。  
  
 などがないことから、暗黙の変換 `Double` に `Int32` ため `Double` よりも広い範囲を持つ `Int32`です。 変換の損失を伴う可能性がある場合でも、明示的な変換演算子を指定できます。  
  
 **X のしないで** 暗黙的なキャストから例外をスローします。  
  
 エンドユーザーがないかもしれません変換が行われているために、何が起こっているかを理解するため非常に困難です。  
  
 **✓ は** スロー <xref:System.InvalidCastException?displayProperty=fullName> 損失を伴う変換でキャスト演算子への呼び出しの結果、その演算子のコントラクトでは、損失を伴う変換することはできません。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)