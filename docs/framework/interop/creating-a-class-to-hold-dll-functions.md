---
title: "DLL 関数を保持するクラスの作成 | Microsoft Docs"
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
  - "COM 相互運用機能, DLL 関数"
  - "COM 相互運用機能, プラットフォーム呼び出し"
  - "DLL 関数"
  - "相互運用 (アンマネージ コードとの), DLL 関数"
  - "相互運用 (アンマネージ コードとの), プラットフォーム呼び出し"
  - "プラットフォーム呼び出し, 作成 (関数のクラスを)"
  - "アンマネージ関数"
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# DLL 関数を保持するクラスの作成
マネージ クラス内の頻繁に使用される DLL 関数をラップすることは、プラットフォームの機能をカプセル化するための効果的な方法です。  ラップは必須ではありませんが、DLL 関数の定義には手間がかかり、エラーの原因にもなりやすいため、クラス ラッパーを用意しておくと便利です。  Visual Basic や C\# を使ってプログラミングしている場合は、DLL 関数をクラスまたは Visual Basic モジュール内で宣言する必要があります。  
  
 クラス内では、呼び出す各 DLL 関数に対して静的メソッドを定義します。  この定義には、メソッド引数を渡すときに使用される文字セットや呼び出し規約などの追加情報を含めることができます。この情報を省略すると、既定の設定が選択されます。  宣言のオプションと、既定の設定の完全なリストについては、「[マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)」を参照してください。  
  
 ラッピングが完了すると、他の静的関数のメソッドを呼び出す場合と同じ方法で、関数のメソッドを呼び出すことができます。  プラットフォーム呼び出しでは、基になるエクスポートされた関数が自動的に処理されます。  
  
 プラットフォーム呼び出しのためにマネージ クラスをデザインする場合は、クラスと DLL 関数との関係を考慮する必要があります。  たとえば、次のように操作できます。  
  
-   既存のクラス内で DLL 関数を宣言する。  
  
-   関数を分離し、検索しやすくするために、DLL 関数ごとに別個のクラスを作成する。  
  
-   論理的なグループを形成し、オーバーヘッドを減らすため、一連の関連する DLL 関数に対して 1 つのクラスを作成する。  
  
 クラスおよびそのメソッドには、任意の名前を付けることができます。  プラットフォーム呼び出しと共に使用する .NET ベースの宣言を構築する方法を示す例については、「[プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)」を参照してください。  
  
## 参照  
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)   
 [DLL 内の関数の識別](../../../docs/framework/interop/identifying-functions-in-dlls.md)   
 [マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [DLL 関数の呼び出し](../../../docs/framework/interop/calling-a-dll-function.md)