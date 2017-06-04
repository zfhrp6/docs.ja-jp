---
title: "方法: 相互運用機能アセンブリをタイプ ライブラリから生成する | Microsoft Docs"
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
  - "インポート (タイプ ライブラリの)"
  - "相互運用機能アセンブリ, 生成"
  - "タイプ ライブラリ"
  - "タイプ ライブラリ インポーター"
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法: 相互運用機能アセンブリをタイプ ライブラリから生成する
[タイプ ライブラリ インポーター \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) は、COM タイプ ライブラリに格納されているコクラスおよびインターフェイスをメタデータに変換するコマンド ライン ツールです。  このツールは、型情報の相互運用機能アセンブリおよび名前空間を自動的に生成します。  クラスのメタデータが利用可能になった後、マネージ クライアントは COM 型のインスタンスを生成し、.NET インスタンスの場合と同様の方法で、そのメソッドを呼び出すことができます。  Tlbimp.exe は、タイプ ライブラリ全体を一度にメタデータに変換しますが、タイプ ライブラリで定義されている型のサブセットの型情報は生成できません。  
  
### タイプ ライブラリから相互運用機能アセンブリを生成するには  
  
1.  次のコマンドを使用します。  
  
     **tlbimp** \<*type\-library\-file*\>  
  
     **\/out:** スイッチを追加することによって LOANLib.dll などの別の名前で相互運用機能アセンブリを生成します。  相互運用機能アセンブリの名前を変更しておくと、元の COM DLL との区別が付けやすくなり、名前の重複によって問題が生じることを防ぐことができます。  
  
## 使用例  
 次のコマンドを使用すると、`Loanlib` 名前空間に Loanlib.dll アセンブリが生成されます。  
  
```  
tlbimp Loanlib.dll  
```  
  
 次のコマンドを使用すると、別の名前 \(LOANLib.dll\) で相互運用機能アセンブリが生成されます。  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## 参照  
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)