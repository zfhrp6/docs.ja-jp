---
title: "相互運用性 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: be95d675d22dedcbf45c8eb1e8fd8d9f5ce0b56c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
<a id="interoperability-c-programming-guide" class="xliff"></a>

# 相互運用性 (C# プログラミング ガイド)
相互運用性は、アンマネージ コードへの既存の投資を保持して活用できるようにします。 共通言語ランタイム (CLR) の制御下で実行されるコードは*マネージ コード*と呼ばれ、CLR の外部で実行されるコードは*アンマネージ コード*と呼ばれます。 アンマネージ コードの例は、COM、COM +、C++ コンポーネント、ActiveX コンポーネント、および Microsoft Win32 API です。  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、プラットフォーム呼び出しサービス、<xref:System.Runtime.InteropServices> 名前空間、C++ 相互運用性、および COM 相互運用性 (COM 相互運用機能) を通して、アンマネージ コードの相互運用を可能にしています。  
  
<a id="in-this-section" class="xliff"></a>

## このセクションの内容  
 [相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 C# のマネージ コードとアンマネージ コードの間で相互運用する方法について説明します。  
  
 [方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Office のプログラミングを容易にするために Visual C# に導入されている機能について説明します。  
  
 [方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 インデックス付きプロパティを使用して、パラメーターを持つ COM プロパティにアクセスする方法について説明します。  
  
 [方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 プラットフォーム呼び出しサービスを使用して、Windows オペレーティング システム上の .wav サウンド ファイルを再生する方法について説明します。  
  
 [チュートリアル: Office のプログラミング](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Excel ブックと、ブックへのリンクを含む Word 文書を作成する方法を示します。  
  
 [COM クラスの例](../../../csharp/programming-guide/interop/example-com-class.md)  
 C# クラスを COM オブジェクトとして公開する方法を示します。  
  
<a id="c-language-specification" class="xliff"></a>

## C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
<a id="see-also" class="xliff"></a>

## 関連項目  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [アンマネージ コードとの相互運用](https://msdn.microsoft.com/library/sd10k43k)   
 [チュートリアル: Office のプログラミング](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
