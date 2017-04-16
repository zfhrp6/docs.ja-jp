---
title: "方法: COM から .NET 型を参照する | Microsoft Docs"
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
  - "COM 相互運用機能, インポート (タイプ ライブラリの)"
  - "COM 相互運用機能, 参照 (.NET 型の)"
  - "インポート (タイプ ライブラリの)"
  - "相互運用 (アンマネージ コードとの), インポート (タイプ ライブラリの)"
  - "相互運用 (アンマネージ コードとの), 参照 (.NET 型の)"
  - "参照 (.NET 型の)"
  - "タイプ ライブラリ"
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法: COM から .NET 型を参照する
クライアント アンド サーバー コードの観点からすると、COM と .NET Framework の違いはほとんどわかりません。  Microsoft Visual Basic クライアントでは、オブジェクト ブラウザーを使って .NET オブジェクトを表示できます。オブジェクト ブラウザーには、オブジェクトのメソッドと構文、プロパティ、およびフィールドが、他の COM オブジェクトの場合と同様に公開されます。  
  
 タイプ ライブラリのインポート処理は、COM タイプ ライブラリにメタデータをエクスポートする場合と同じツールを使用しますが、C\+\+ クライアントの場合の方がやや複雑です。  アンマネージ C\+\+ クライアントから .NET オブジェクトのメンバーを参照するには、**\#import** ディレクティブが含まれている TLB ファイル \(Tlbexp.exe により生成\) を参照します。  C\+\+ からタイプ ライブラリを参照する場合は、**raw\_interfaces\_only** オプションを指定するか、または基底クラス ライブラリの Mscorlib.tlb 内の定義をインポートする必要があります。  
  
### ライブラリをインポートするには  
  
-   **\#import** ディレクティブで **raw\_interfaces\_only** オプションを指定します。  次のように記述します。  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     または  
  
-   Mscorlib.tlb の \#import ディレクティブを含めます。  次のように記述します。  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## 参照  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [COM へのアセンブリの登録](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/ja-jp/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/ja-jp/fb63564c-c1b9-4655-a094-a235625882ce)