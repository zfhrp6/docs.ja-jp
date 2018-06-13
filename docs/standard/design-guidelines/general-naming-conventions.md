---
title: 一般的な名前付け規則
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc54b8bdc96a5038dc75111d9833e70e7ffd2e9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578041"
---
# <a name="general-naming-conventions"></a>一般的な名前付け規則
このセクションでは、一般的な名前付け規則単語の選択に関連する言語固有の名前を使用しないようにする方法の省略形と頭字語、および推奨事項の使用に関するガイドラインについて説明します。  
  
## <a name="word-choice"></a>単語の選択  
 **✓ しないで**読みやすい識別子の名前を選択します。  
  
 という名前のプロパティなど、`HorizontalAlignment`は英語 - よりも読みやすく`AlignmentHorizontal`です。  
  
 **✓ しないで**簡潔さよりも読みやすさを優先します。  
  
 プロパティ名`CanScrollHorizontally`がよりも良い`ScrollableX`(x 軸にあいまいな参照)。  
  
 **X しないで**アンダー スコア、ハイフン、またはその他の英数字以外の文字を使用します。  
  
 **X しないで**ハンガリアン記法を使用します。  
  
 **避け x**広くのキーワードと競合する識別子を使用してプログラミング言語を使用します。  
  
 ルール 4 の共通言語仕様 (CLS)、に従って準拠のすべての言語は、その言語のキーワードを識別子として使用する名前付きの項目にアクセスできるようにするメカニズムを提供する必要があります。 C# の場合、たとえば、使用して、@ ここではエスケープ メカニズムとしてマークします。 ただし、勧めまだメソッドを使用して、エスケープ シーケンスが指定されていない場合よりも非常に困難になっているために、一般的なキーワードを回避することをお勧めします。  
  
## <a name="using-abbreviations-and-acronyms"></a>略称や頭字語を使用します。  
 **X しないで**識別子名の一部としての省略形または短縮形を使用します。  
  
 たとえば、使用して`GetWindow`なく`GetWin`です。  
  
 **X しないで**広く受け入れられていると偶数の場合は、必要な場合にのみではない任意の頭字語を使用します。  
  
## <a name="avoiding-language-specific-names"></a>言語固有の名前の回避  
 **✓ しないで**型名に言語固有のキーワードではなく、意味的にわかりやすい名前を使用します。  
  
 たとえば、`GetLength`よりも優れた名前は、`GetInt`です。  
  
 **✓ しないで**まれなケース識別子には、その型以外の意味があるない場合に言語固有の名前ではなく、汎用の CLR 型名を使用します。  
  
 たとえば、メソッドへの変換<xref:System.Int64>という名前を付ける必要があります`ToInt64`ではなく、 `ToLong` (ため<xref:System.Int64>、c# の CLR 名です-特定のエイリアス`long`)。 次の表は、CLR 型名 (だけでなく c#、Visual Basic、および C++ の対応する型名) を使用していくつかの基本データ型を示します。  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**オブジェクト**|**オブジェクト**|**オブジェクト**|  
  
 **✓ しないで**など、共通名を使用して`value`または`item`、まれなケース識別子は特別な意味を持たないし、パラメーターの型が重要でないときに、型名を繰り返しではなくです。  
  
## <a name="naming-new-versions-of-existing-apis"></a>既存の Api の新しいバージョンの名前を付ける  
 **✓ しないで**既存の API の新しいバージョンを作成するときに、古い API への名前を使用します。  
  
 これにより、Api の間のリレーションシップを強調表示します。  
  
 **✓ しないで**を既存の API の新しいバージョンを示すプレフィックスではなく、サフィックスを追加することを希望します。  
  
 これは、役立ちます探索ドキュメントについてを参照するときに Intellisense を使用してまたはします。 古いバージョンの API はほとんどのブラウザーおよび Intellisense は、アルファベット順に識別子を表示するため、新しい Api の近くに編成できます。  
  
 **✓ を検討してください**サフィックスまたはプリフィックスを追加する代わりに、まったく新しいが意味のある識別子を使用します。  
  
 **✓ しないで**の数値のサフィックスを使用して、既存の API の新しいバージョンを指定する、API の既存の名前 (つまり、業界標準である) 場合は、意味のある唯一の名前は、どの意味を追加する場合は、サフィックス (または、名前を変更する) アプリの場合に特にropriate オプション。  
  
 **X しないで**"Ex"(または類似した) を使用して、同じ API の以前のバージョンと区別する識別子のサフィックスです。  
  
 **✓ しないで**32 ビット整数の代わりに 64 ビット整数 (長整数) で動作する Api のバージョンを導入するときに、「64」サフィックスを使用します。 のみ、既存の 32 ビット API が存在する場合に、この方法を実行する必要があります。しないことを 64 ビット バージョンのみでの新しい api です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
