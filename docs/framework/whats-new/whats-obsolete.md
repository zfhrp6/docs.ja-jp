---
title: ".NET Framework クラス ライブラリの互換性のために残されている機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用されなくなった [.NET Framework]"
  - "互換性のために残されている [.NET Framework]"
  - "互換性のために残されている機能 [.NET Framework]"
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework クラス ライブラリの互換性のために残されている機能
.NET Framework は進化しています。  バージョンが新しくなるたびに、新しい機能を提供する新しい型と新しいメンバーが追加されています。  既存の型とそのメンバーも変更されています。  たとえば、一部の型は、その型がサポートするテクノロジが新しいテクノロジに置き換えられることで重要度が下がり、一部のメソッドは、より便利な新しいメソッドまたはより多くの機能を備えた新しいメソッドに置き換えられています。  
  
 .NET Framework と共通言語ランタイムでは、下位互換性をサポートするように努めています \(.NET Framework の特定のバージョンで開発したアプリケーションを、.NET Framework の次期バージョンで実行できるようにするためです\)。  そのため、型または型のメンバーを単純に削除することはできません。  そこで、.NET Framework では、型または型のメンバーが使用されなくなったことを示すために、その型またはメンバーを旧式 \(互換性のために残されている\) または非推奨として指定しています。  型またはメンバーを非推奨とする場合は、開発者がその型またはメンバーが削除予定であることを認識してその削除に対応できるように、指定を行う必要があります。  ただし、そのような型またはメンバーを使用する既存のコードは、.NET Framework の次期バージョンで引き続き実行できます。  
  
> [!NOTE]
>  *旧式* \(互換性のために残されている\) という用語と*非推奨*という用語は、.NET Framework の型とメンバーに対して使用する場合は同じ意味です。  
  
## ObsoleteAttribute 属性  
 .NET Framework では、型または型のメンバーが旧式であることを示すために、その型またはメンバーに <xref:System.ObsoleteAttribute> 属性を指定します。  この属性が型またはメンバーに適用されている場合、その型またはメンバーは .NET Framework の将来のバージョンで削除される予定であることを意味します。ただし、そのメンバーを使用するコンパイル済みコードに影響はありません。  
  
 型または型のメンバーが旧式であることを示す以外に、<xref:System.ObsoleteAttribute> は、その型またはメンバーが含まれているソース コードをコンパイラで処理する方法を定義します。  コードをコンパイルするが警告メッセージを出力するようにすることも、旧式の型またはメンバーの使用をエラーとして扱うこともできます。  前者の場合、コードを正常にコンパイルできますが、警告メッセージによって型またはメンバーが旧式であることが示されます。  後者の場合、コンパイルは失敗します。  
  
 コンパイルで警告メッセージではなくエラーが生成される場合でも、<xref:System.ObsoleteAttribute> は実行時の動作には影響を与えません。  つまり、旧式の型またはメンバーを使用しているが正常にコンパイルされたアプリケーションは、常に正常に実行されます。  旧式の型またはメンバーを使用するアプリケーションを再コンパイルしようとした場合にのみ失敗します。  
  
## 旧式の型とメンバーを処理する方法  
 既存のコードをアップグレードし、再コンパイルする場合に、コンパイラの警告を生成する旧式の型またはメンバーをアプリケーションで使用しても、まったく問題ありません。  ただし、コンパイラの警告メッセージを確認して、アプリケーション コードを変更する必要があるかどうか判断する必要があります。  代わりとなる適切な方法がメッセージに示されていない場合は、次のいずれかの操作を行う必要があります。  
  
-   可能であれば、コードを変更して旧式の型またはメンバーの使用を止めます。  
  
     または  
  
-   このテクノロジ分野に関するドキュメントを確認して、非推奨の機能の使用に対する対応方法を決定します。  
  
 既存のコードは、.NET Framework の新しいバージョンに対して再コンパイルすることはできません。  代わりに、既存のコンパイル済みコードの実行対象である .NET Framework のバージョンを指定できます。  たとえば、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] に対してコンパイルされた app1.exe というアプリケーションがあり、このアプリケーションを [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象に実行する必要があるとします。  この場合、次の手順が必要です。  
  
1.  メイン実行可能ファイルの構成ファイルを作成し、その名前を *appName*.exe.config にします。*appName* は、アプリケーションの実行可能ファイルの名前です。  このトピックの例の app1.exe というアプリケーションの場合は、app1.exe.config という名前の構成ファイルを作成します。  
  
2.  次のコードを構成ファイルに追加します。  
  
    ```  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 .NET Framework の特定のバージョンを対象とするために `version` 属性に割り当てることができる文字列値を次の表に示します。  
  
|||  
|-|-|  
|.NET Framework のバージョン|`version` 文字列|  
|4.5 \(4.5.1 および他のポイント リリースを含む\)|v4.0|  
|4|v4.0|  
|3.5|v2.0.50727|  
|2.0|v2.0.50727|  
|1.1|v1.1.4322|  
|1|v1.0.3705|  
  
## .NET Framework 4.5 の互換性のために残されている機能の一覧  
 [Obsolete Types \(互換性のために残されている型\)](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Obsolete Members \(互換性のために残されているメンバー\)](../../../docs/framework/whats-new/obsolete-members.md)  
  
## 以前のバージョンの互換性のために残されている機能の一覧  
 [.NET Framework 4 で互換性のために残されている型](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [.NET Framework 4 で互換性のために残されているメンバー](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [.NET Framework 3.5 廃止予定の一覧](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [.NET Framework 2.0 廃止予定の一覧](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## 参照  
 [\<supportedRuntime\> 要素](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)