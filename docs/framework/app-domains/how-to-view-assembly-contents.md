---
title: "方法 : アセンブリの内容を表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ マニフェスト、表示 (情報を)"
  - "Ildasm.exe"
  - "MSIL 逆アセンブラー"
  - "アセンブリ [.NET Framework]、表示 (内容を)"
  - "表示 (アセンブリ情報を)"
  - "MSIL"
  - "表示 (MSIL 情報を)"
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : アセンブリの内容を表示する
[Ildasm.exe \(IL 逆アセンブラー\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、ファイル内の MSIL \(Microsoft Intermediate Language\) 情報を表示できます。  内容を調べる対象のファイルがアセンブリの場合、この情報には、アセンブリの属性とほかのモジュールおよびアセンブリへの参照が含まれることがあります。  この情報は、ファイルがアセンブリまたはアセンブリの一部かどうか、およびファイルにほかのモジュールまたはアセンブリへの参照があるかどうかを判断するために役立ちます。  
  
### Ildasm.exe を使用してアセンブリの内容を表示するには  
  
1.  コマンド \<プロンプト\> に **\[ildasm\]** の*アセンブリ名*。  たとえば、次のコマンドでは、`Hello.exe` アセンブリが逆アセンブルされます。  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### アセンブリ マニフェストの情報を表示するには  
  
1.  MSIL 逆アセンブラー ウィンドウで、マニフェストのアイコンをダブルクリックします。  
  
## 使用例  
 次の例では、基本の "Hello, World" プログラムを使用します。  プログラムをコンパイルしてから、Ildasm.exe を使用して Hello.exe アセンブリを逆アセンブルし、アセンブリ マニフェストを参照します。  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Hello.exe アセンブリに対して ildasm.exe コマンドを実行し、IL 逆アセンブラー ウィンドウでマニフェストのアイコンをダブルクリックすると、次の内容が出力されます。  
  
```  
  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
  
```  
  
 次の表は、例で使用した Hello.exe アセンブリのアセンブリ マニフェストにある各ディレクティブの説明です。  
  
|ディレクティブ|説明|  
|-------------|--------|  
|**.assembly extern \<**の*アセンブリ名* **\>**|現在のモジュールによって参照される項目を含む別のアセンブリを指定します \(この例では `mscorlib`\)。|  
|**.publickeytoken \<** *トークン* **\>**|参照されるアセンブリの実際のキーのトークンを指定します。|  
|**.ver \<**の*バージョン番号* **\>**|参照されるアセンブリのバージョン番号を指定します。|  
|**.assembly \<**の*アセンブリ名* **\>**|アセンブリ名を指定します。|  
|**.hash algorithm \<** *int32 値* **\>**|使用されるハッシュ アルゴリズムを指定します。|  
|**.ver \<**の*バージョン番号* **\>**|アセンブリのバージョン番号を指定します。|  
|**.module \<**の*ファイル名* **\>**|アセンブリを構成するモジュールの名前を指定します。  この例では、アセンブリは 1 つのファイルだけで構成されています。|  
|**.subsystem \<** *値* **\>**|プログラムが必要とするアプリケーション環境を指定します。  この例では、値 3 でこの実行可能ファイルがコンソールで実行されることを示します。|  
|**.corflags**|現在メタデータ内で予約済みのフィールドです。|  
  
 アセンブリ マニフェストは、アセンブリの内容に応じて、多くの異なるディレクティブを格納できます。  アセンブリ マニフェストに含まれる多様なディレクティブの一覧については、ヨーロッパ電子計算機工業会 \(ECMA : European Computer Manufacturer Association\) のドキュメント、特に「Partition II: Metadata Definition and Semantics」および「Partition III: CIL Instruction Set」を参照してください。  ドキュメントはオンラインで入手できます。; MSDN [ECMA C\# および共通言語基盤 \(CLI\) 標準](http://go.microsoft.com/fwlink/?LinkID=99212) および [" Standard ECMA\-335 \- Common Language Infrastructure \(CLI\)](http://go.microsoft.com/fwlink/?LinkID=65552) Standards \(Web サイトを参照してください。  
  
## 参照  
 [Application Domains and Assemblies](http://msdn.microsoft.com/ja-jp/433b04ae-4ba8-4849-9dbd-79194f240346)   
 [アプリケーション ドメインとアセンブリに関する方法のトピック](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)   
 [Ildasm.exe \(IL 逆アセンブラー\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)