---
title: "方法: バイト配列を int に変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "バイト配列 [C#], 変換 (int に)"
  - "変換 [C#], バイト配列 (int に)"
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: バイト配列を int に変換する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の例では、<xref:System.BitConverter> クラスを使用してバイト配列を [int](../../../csharp/language-reference/keywords/int.md) に変換する方法、およびバイト配列に戻す方法を示しています。  ネットワークに接続せずにバイトを読み取った場合などは、その後バイトから組み込みデータ型への変換が必要になる場合もあります。  この例の [ToInt32\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt32(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False) メソッド以外にも、バイト \(バイト配列\) を他の組み込み型に変換するメソッドがあります。<xref:System.BitConverter> クラス内のそのようなメソッドを次の表に示します。  
  
|戻される型|メソッド|  
|-----------|----------|  
|`bool`|[ToBoolean\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToBoolean(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`char`|[ToChar\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToChar(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`double`|[ToDouble\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToDouble(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`short`|[ToInt16\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt16(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`int`|[ToInt32\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt32(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`long`|[ToInt64\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt64(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`float`|[ToSingle\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToSingle(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`ushort`|[ToUInt16\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToUInt16(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`uint`|[ToUInt32\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToUInt32(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
|`ulong`|[ToUInt64\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToUInt64(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False)|  
  
## 使用例  
 この例ではバイト配列を初期化します。コンピューター アーキテクチャがリトル エンディアンの場合 \(つまり最下位バイトから先に格納される場合\)、配列を反転します。次に、[ToInt32\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt32(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False) メソッドを呼び出して、配列内の 4 バイトを `int` に変換します。  [ToInt32\(Byte\[\], Int32\)](assetId:///M:System.BitConverter.ToInt32(System.Byte[],System.Int32)?qualifyHint=False&autoUpgrade=False) の 2 番目の引数は、バイト配列の開始インデックスを指定します。  
  
> [!NOTE]
>  出力は、コンピューターのアーキテクチャのエンディアンによって異なる場合があります。  
  
 [!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## 使用例  
 この例では、<xref:System.BitConverter> クラスの <xref:System.BitConverter.GetBytes%28System.Int32%29> メソッドを呼び出して、`int` をバイトの配列に変換します。  
  
> [!NOTE]
>  出力は、コンピューターのアーキテクチャのエンディアンによって異なる場合があります。  
  
 [!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## 参照  
 <xref:System.BitConverter>   
 <xref:System.BitConverter.IsLittleEndian>   
 [型](../../../visual-basic/reference/command-line-compiler/index.md)