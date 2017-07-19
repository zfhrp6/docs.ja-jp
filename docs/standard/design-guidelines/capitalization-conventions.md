---
title: "大文字と小文字の表記規則 | Microsoft Docs"
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
  - "camel 形式で名前 [.NET Framework]"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] 大文字と小文字"
  - "Pascal 形式名 [.NET Framework]"
  - "大文字小文字の区別、大文字と小文字の表記規則"
  - "大文字と小文字の名前 [.NET Framework]"
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 大文字と小文字の表記規則
単純なメソッドを使用するためのこの章のレイアウトのガイドラインの場合、型、メンバー、および読みやすいパラメーターの識別子を作成、一貫した適用時にされます。  
  
## 識別子の大文字と小文字の規則  
 識別子内の単語を区別するためには、識別子内の各単語の最初の文字を大文字に変換します。 アンダー スコアは、単語を区別するために使用しないでまたは識別子で任意の場所に言えば、します。 識別子の使用によって、識別子の大文字にする 2 つの適切な方法があります。  
  
-   Pascal 表記を使用  
  
-   camel 表記  
  
 パラメーター名以外のすべての識別子に使用する、pascal 表記を使用規則は、次の例に示すように、\(2 文字の長さを頭字語を含む\) の各単語の最初の文字を大文字になります。  
  
 `PropertyDescriptor`   
 `HtmlTag`  
  
 特殊なケースは、次の識別子に示すように、両方の文字を大文字に、2 文字の頭字語に。  
  
 `IOStream`  
  
 パラメーター名専用に使用される、camel 表記規則では、次の例に示すように、最初の単語以外の各単語の最初の文字が大文字にします。 例に示すも camel 形式の識別子で始まる 2 文字の頭字語は小文字の両方です。  
  
 `propertyDescriptor`   
 `ioStream`   
 `htmlTag`  
  
 **✓ は** pascal 表記を使用を使用して、すべてのパブリック メンバー、型、および名前空間名の複数の単語で構成されます。  
  
 **✓ は** パラメーター名の camel 表記を使用します。  
  
 次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。  
  
|識別子|大文字小文字の区別|例|  
|---------|---------------|-------|  
|Namespace|Pascal 形式|`namespace System.Security { ... }`|  
|型|Pascal 形式|`public class StreamReader { ... }`|  
|インターフェイス|Pascal 形式|`public interface IEnumerable { ... }`|  
|メソッド|Pascal 形式|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|プロパティ|Pascal 形式|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|イベント|Pascal 形式|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|フィールド|Pascal 形式|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列挙値|Pascal 形式|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|パラメーター|キャメル形式|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## 複合語の大文字と一般的な用語  
 ほとんどの複合語は、大文字と小文字の単語として扱われます。  
  
 **X のしないで** いわゆる閉じた形式の複合語の各単語を大文字に変換します。  
  
 これらは、複合語がエンドポイントなどの 1 つの単語として書き込まれます。 大文字と小文字のガイドライン、するためには、1 つの単語として閉じた形式の複合語を扱います。 複合語が閉形式で記述されたかどうかを判断するのにには、現在の辞書を使用します。  
  
|Pascal 形式|キャメル形式|Not|  
|---------------|------------|---------|  
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
  
## 大文字と小文字の区別  
 CLR で実行できる言語は、いくつかが、大文字小文字の区別をサポートするために必要はありません。 でも、言語サポートする場合、他の言語、フレームワークにアクセスする可能性を持っていません。 したがって、外部アクセス可能なすべての Api は、同じコンテキストで 2 つの名前を区別するためだけの場合に使用できません。  
  
 **X のしないで** すべてのプログラミング言語が大文字小文字を区別と見なされます。 できません。 名前は、単独で大文字と小文字が異なることはできません。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)