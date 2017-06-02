---
title: "一般的な名前付け規則 | Microsoft Docs"
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
  - "名前 [.NET Framework] の競合"
  - "型名の競合"
  - "言語固有の型名"
  - "名前付けのガイドラインについては、名前 [.NET Framework]"
  - "名前 [.NET Framework] の省略形"
  - "省略形名前付けのガイドライン"
  - "頭字語の名前付けのガイドライン"
  - "ハンガリアン記法"
  - "型名の名前 [.NET Framework]"
  - "頭字語の名前 [.NET Framework]"
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 一般的な名前付け規則
このセクションでは、一般的な名前付け規則単語の選択に関連する言語固有の名前を使用しないようにする方法の省略形と頭字語、および推奨事項の使用に関するガイドラインについて説明します。  
  
## 単語の選択  
 **✓ は** 読みやすい識別子の名前を選択します。  
  
 という名前のプロパティなど `HorizontalAlignment` 英語 \- よりも読みやすく、 `AlignmentHorizontal`です。  
  
 **✓ は** 簡潔さよりも読みやすさを優先します。  
  
 プロパティ名 `CanScrollHorizontally` よりも優れて `ScrollableX` \(x 軸にあいまいな参照\)。  
  
 **X のしないで** アンダー スコア、ハイフン、またはその他の英数字以外の文字を使用します。  
  
 **X のしないで** ハンガリアン記法を使用します。  
  
 **X 回避** 広くのキーワードと競合する識別子を使用してプログラミング言語を使用します。  
  
 ルール 4 の共通言語仕様 \(CLS\)、に従って準拠のすべての言語は、その言語のキーワードを識別子として使用する名前付きの項目にアクセスできるようにするメカニズムを提供する必要があります。 C\# の場合、たとえば、使用して、ここではエスケープ メカニズムとして @ です。 ただしよりも、エスケープ シーケンスでメソッドを使用するよりずっと困難であるために、一般的なキーワードを回避することをお勧めではまだです。  
  
## 省略形と頭字語を使用します。  
 **X のしないで** 識別子名の一部としての省略形または短縮形を使用します。  
  
 たとえば、使用して `GetWindow` なく `GetWin`です。  
  
 **X のしないで** 広く受け入れられているとは、必要な場合にのみの場合でもある頭字語を使用します。  
  
## 言語固有の名前を回避します。  
 **✓ は** 型の名前に言語固有のキーワードではなく、意味的にわかりやすい名前を使用します。  
  
 たとえば、 `GetLength` よりも優れた名前は、 `GetInt`です。  
  
 **✓ は** 識別子には、その型以外の意味があるないときは、まれなケースで言語固有の名前ではなく、汎用の CLR 型名を使用します。  
  
 変換するメソッドなど、 <xref:System.Int64> はという名前で `ToInt64`, ではなく、 `ToLong` \(ため <xref:System.Int64> 、c\# の CLR 名である\-特定のエイリアス `long`\)。 次の表は、CLR 型名 \(およびその c\#、Visual Basic および C\+\+ の対応する型名\) を使用していくつかの基本データ型を表示します。  
  
|C\#|Visual Basic|C\+\+|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**短い名前**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**整数**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**\_\_int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned \_\_int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**倍精度浮動小数点型**|**double**|**倍精度浮動小数点型**|  
|**bool**|**ブール型**|**bool**|**ブール型**|  
|**char**|**Char**|**wchar\_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**オブジェクト**|**オブジェクト**|**オブジェクト**|  
  
 **✓ は**  共通名を使用して `value` または `item`, 、繰り返し型の名前識別子が特別な意味を持たないし、パラメーターの型が重要ではないまれなケースではなく。  
  
## 既存の Api の新しいバージョンの名前を付ける  
 **✓ は** 既存の API の新しいバージョンを作成するときに、古い API のような名前を使用します。  
  
 これにより、Api の間のリレーションシップを強調表示します。  
  
 **✓ は** 既存の API の新しいバージョンを示すプレフィックスではなく、サフィックスの追加を希望します。  
  
 これは、ドキュメントについてを参照するときに検出、コンピュータは Intellisense を使用するか。 古いバージョンの API はほとんどのブラウザーおよび Intellisense は、アルファベット順に識別子を表示するために、新しい Api の近くに整理されます。  
  
 **✓ を検討してください** サフィックスまたはプレフィックスを追加する代わりに、まったく新しいが意味のある識別子を使用します。  
  
 **✓ は** 数値のサフィックスを使用して、既存の API の名前 \(つまり、業界標準である\) 場合は、意味のある唯一の名前は、追加、意味のある場合はサフィックス \(または名前を変更する\)、適切なオプション場合は特に、既存の API の新しいバージョンを示します。  
  
 **X のしないで** "Ex"\(または類似\) を使用して、同じ API の以前のバージョンを区別するために識別子のサフィックスです。  
  
 **✓ は** 32 ビット整数ではなく、64 ビット整数 \(長整数\) を操作する Api のバージョンを導入するときは、「64」サフィックスを使用します。 のみ、既存の 32 ビット API が存在するときに、この方法を実行する必要があります。64 ビット版のみで新しい Api のことを実行しません。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)