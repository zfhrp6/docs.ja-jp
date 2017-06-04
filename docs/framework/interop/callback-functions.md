---
title: "コールバック関数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "callback 関数"
  - "プラットフォーム呼び出し, 呼び出し (アンマネージ関数の)"
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# コールバック関数
コールバック関数は、アンマネージ DLL 関数が作業を完了できるようにするためのマネージ アプリケーション内のコードです。  コールバック関数への呼び出しは、マネージ アプリケーションから DLL 関数を通じて間接的に渡され、マネージ実装に返されます。  プラットフォーム呼び出しで呼び出される DLL 関数の中には、マネージ コードにコールバック関数が記述されていないと、正しく実行できない関数があります。  
  
 ほとんどの DLL 関数の場合、マネージ コードから呼び出すには関数のマネージ定義を作成して、それを呼び出します。  この処理は簡単です。  
  
 コールバック関数を必要とする DLL 関数を使用する場合は、追加の手順が必要になります。  最初に、関数のドキュメントを参照して、その関数がコールバックを必要とするかどうかを判断します。  次に、マネージ アプリケーション内にコールバック関数を作成します。  最後に、コールバック関数に引数としてポインターを渡し、DLL 関数を呼び出します。  これらのステップを要約した図を次に示します。  
  
 ![プラットフォーム呼び出しコールバック](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
コールバック関数とその実装  
  
 コールバック関数は、繰り返し実行されるタスクがある状況での使用に適しています。  もう 1 つの一般的な使い方として、Win32 API の **EnumFontFamilies**、**EnumPrinters**、**EnumWindows** などの列挙関数と組み合わせる方法があります。  **EnumWindows** 関数は、コンピューター上の既存のウィンドウすべてで列挙し、コールバック関数を呼び出して各ウィンドウでタスクを実行します。  手順と例については、「[方法 : コールバック関数を実装する](../../../docs/framework/interop/how-to-implement-callback-functions.md)」を参照してください。  
  
## 参照  
 [方法: コールバック関数を実装する](../../../docs/framework/interop/how-to-implement-callback-functions.md)   
 [DLL 関数の呼び出し](../../../docs/framework/interop/calling-a-dll-function.md)