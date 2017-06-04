---
title: "COM への .NET Framework コンポーネントの公開 | Microsoft Docs"
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
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "公開 (COM に .NET Framework コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), 公開 (.NET Framework コンポーネントを)"
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# COM への .NET Framework コンポーネントの公開
.NET 型を作成することと、その型をアンマネージ コードから処理することは、開発者にとってはまったく別の作業です。  このセクションでは、COM クライアントと相互運用できるマネージ コードを作成するためのヒントを示します。  
  
-   [相互運用のための .NET 型の要件](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
  
     COM に対して公開するすべてのマネージ型、マネージ メソッド、マネージ プロパティ、マネージ フィールド、およびマネージ イベントは、パブリックとしてください。  型は、パブリックな既定のコンストラクターを持っている必要があります。このコンストラクターが、COM を通じて呼び出すことができる唯一のコンストラクターです。  
  
-   [相互運用固有の属性の適用](../../../docs/framework/interop/applying-interop-attributes.md)  
  
     マネージ コード内でカスタム属性を使用すると、コンポーネントの相互運用性を拡張できます。  
  
-   [COM 用のアセンブリのパッケージ化](../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
  
     作成したアセンブリの参照と配置に必要な手順の要約を COM 開発者が必要とする場合があります。  
  
 補足として、COM クライアントからのマネージ型の処理に関連する作業を説明します。  
  
#### COM からマネージ型を処理するには  
  
1.  [アセンブリを COM に登録します](../../../docs/framework/interop/registering-assemblies-with-com.md)。  
  
     アセンブリ内の型 \(およびタイプ ライブラリ\) は、デザイン時に登録する必要があります。  インストーラーでアセンブリを登録しない場合は、Regasm.exe を使うように COM 開発者に指示してください。  
  
2.  [COM から .NET 型を参照します](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)。  
  
     COM 開発者は、現在使用しているのと同じツールおよび方法で、アセンブリ内の型を参照できます。  
  
3.  [.NET オブジェクトを呼び出します](http://msdn.microsoft.com/ja-jp/40c9626c-aea6-4bad-b8f0-c1de462efd33)。  
  
     COM 開発者は、アンマネージ型のメソッドを呼び出す場合と同じ方法で、.NET オブジェクトのメソッドを呼び出すことができます。  たとえば、COM の **CoCreateInstance** API は、.NET オブジェクトをアクティブにします。  
  
4.  [COM からアクセスできるようにアプリケーションを配置します](http://msdn.microsoft.com/ja-jp/fb63564c-c1b9-4655-a094-a235625882ce)。  
  
     厳密な名前のアセンブリは、グローバル アセンブリ キャッシュにインストールできます。また、発行者からの署名が必要です。  厳密な名前のないアセンブリは、クライアントのアプリケーション ディレクトリにインストールする必要があります。  
  
## 参照  
 [アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)   
 [COM 相互運用機能のサンプル: COM クライアントおよび .NET サーバー](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)