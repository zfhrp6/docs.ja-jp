---
title: 大文字の使用規則
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef7913a2601c3a791cb028b4074ce37b9e9421b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575285"
---
# <a name="capitalization-conventions"></a>大文字の使用規則
単純なメソッドを使用するためのこの章のレイアウトのガイドライン場合は、型、メンバー、およびパラメーターについて読みやすくする識別子を一貫して、適用されるときにします。  
  
## <a name="capitalization-rules-for-identifiers"></a>識別子の大文字と小文字の規則  
 識別子内の単語を区別するために、識別子内の各単語の最初の文字を大文字に変換します。 アンダー スコアは、単語を区別するために使用しないでくださいまたは識別子で任意の場所に言えば、します。 これには識別子の使用によって、識別子を大文字に変換する 2 つの適切な方法があります。  
  
-   Pascal 表記を使用  
  
-   camel 表記  
  
 パラメーターの名前を除いて、すべての識別子を使用する、pascal 表記を使用規則は、次の例に示すように、(2 文字の長さで経由での頭字語を含む) の各単語の最初の文字を大文字になります。  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 特殊なケースは id に、次に示すように両方の文字を大文字にする、2 文字の頭字語に。  
  
 `IOStream`  
  
 パラメーター名専用に使用される、camel 表記規則は、次の例に示すように、最初の単語以外の各単語の最初の文字を大文字にします。 例に示すも camel 形式の識別子を開始する 2 文字の頭字語は小文字の両方になります。  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ しないで**すべてパブリック メンバー、種類、および名前空間の名前を複数の単語で構成される pascal 表記を使用を使用します。  
  
 **✓ しないで**パラメーター名の camel 表記を使用します。  
  
 次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。  
  
|識別子|大文字小文字の区別|例|  
|----------------|------------|-------------|  
|名前空間|Pascal|`namespace System.Security { ... }`|  
|型|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|メソッド|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|プロパティ|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|event|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|フィールド|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列挙値|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|パラメーター|Camel 形式|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>複合語の大文字と一般的な用語  
 ほとんどの複合語は、大文字と小文字の目的で 1 つの単語として扱われます。  
  
 **X しないで**いわゆる閉じたフォームの複合語内の各単語を大文字に変換します。  
  
 これらは、エンドポイントなど、1 つの単語として書き込まれる複合語です。 大文字と小文字のガイドラインについては、目的には、1 つの単語として閉じられた形式の複合語を扱います。 現在のディクショナリを使用すると、複合語が閉じたフォームで記述されたかどうかを判断できます。  
  
|Pascal|Camel 形式|Not|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>大文字と小文字の区別  
 CLR で実行できる言語は、いくつかが、大文字小文字の区別をサポートする必要はありません。 でも使用する言語でサポートされる場合、その他の言語、フレームワークにアクセスする必要ありません。 したがって、外部からアクセス可能であるすべての Api は、場合、同じコンテキストで 2 つの名前を区別するために単独で使用できません。  
  
 **X しないで**すべてのプログラミング言語が大文字小文字を区別があると仮定します。 しかし、そうではありません。 名前は、大文字と小文字だけでは区別できません。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
