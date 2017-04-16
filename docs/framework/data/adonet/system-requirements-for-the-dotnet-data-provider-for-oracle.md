---
title: ".NET Framework Data Provider for Oracle のシステム要件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# .NET Framework Data Provider for Oracle のシステム要件
.NET Framework Data Provider for Oracle を使用するには、MDAC \(Microsoft Data Access Components\) のバージョン 2.6 以降が必要です。  MDAC 2.8 SP1 をインストールすることをお勧めします。  
  
 Oracle 8i Release 3 \(8.1.7\) Client 以降もインストールする必要があります。  
  
 UTF16 は Oracle 9i の新機能なので、Oracle 9i 以前のバージョンの Oracle Client ソフトウェアでは UTF16 データベースにアクセスできません。  この機能を使用するには、お使いのクライアント ソフトウェアを Oracle 9i 以降にアップグレードする必要があります。  
  
## Data Provider for Oracle と Unicode データの使用  
 .NET Framework Data Provider for Oracle および Oracle クライアント ライブラリを使用するときに考慮が必要な、Unicode に関連する問題の一覧を以下に示します。  詳細については、Oracle のドキュメントを参照してください。  
  
### 接続文字列の属性に Unicode 値を設定する  
 Oracle を操作する場合、接続文字列の属性を使用し、  
  
```  
Unicode=True   
```  
  
 UTF\-16 モードで Oracle クライアント ライブラリを初期化することができます。  これにより、Oracle クライアント ライブラリで、マルチバイト文字列の代わりに UTF\-16 \(UCS\-2 とよく似ています\) が使用できるようになります。  新たに変換作業を行わなくても、Data Provider for Oracle で Oracle のコード ページを常に使用できます。  この構成は、Oracle 9i クライアントを使用して、AL16UTF16 の代替文字セットを持つ Oracle 9i データベースと通信する場合に動作します。  Oracle 9i クライアントが Oracle 9i サーバーと通信するとき、Unicode の **CommandText** 値を Oracle 9i サーバーが使用する適切なマルチバイト文字セットに変換するためのリソースが別に必要になります。  安全な構成が確保されていることがわかっている場合は、`Unicode=True` を接続文字列に追加することにより回避することができます。  
  
### Oracle クライアントと Oracle サーバーのバージョンの混在  
 Oracle 8i クライアントは、サーバーの各国語文字セットが AL16UTF16 \(Oracle 9i の既定の設定\) に指定されている場合、Oracle 9i データベースの **NCHAR**、**NVARCHAR2**、または **NCLOB** データにアクセスできません。  UTF\-16 文字セットのサポートは Oracle 9i まで導入されなかったため、Oracle 8i クライアントでは読み取れません。  
  
### UTF\-8 データの使用  
 代替文字セットを設定するには、レジストリ キー HKEY\_LOCAL\_MACHINE\\SOFTWARE\\ORACLE\\HOMEID\\NLS\_LANG を UTF8 に設定します。  詳細については、ご使用のプラットフォームに関する Oracle のインストール ノートを参照してください。  既定の設定は、Oracle Client ソフトウェアのインストールに使用する言語の基本文字セットになっています。  接続するデータベースの各国語文字セットと言語が一致するように設定されていないと、パラメーターと列の組み合わせは、各国語文字セットではなくプライマリ データベースの文字セットでデータを送受信します。  
  
### OracleLob で更新できるのは Full 文字列のみです。  
 ユーザビリティ上の理由から、<xref:System.Data.OracleClient.OracleLob> オブジェクトは .NET Framework Stream クラスを継承して、**ReadByte** および **WriteByte** メソッドを提供します。  Oracle **LOB** オブジェクトのセクションで動作する **CopyTo** や **Erase** などのメソッドも実装します。  対照的に、Oracle クライアント ソフトウェアには、文字列 **LOB** \(**CLOB** および **NCLOB**\) で使用できる多くの API があります。  ただし、これらの API は full 文字列でのみ動作します。  こうした違いにより、Data Provider for Oracle の実装では、バイトと同様に UTF\-16 を使用できるよう **Read** および **ReadByte** をサポートしています。  ただし、**OracleLob** オブジェクトのその他のメソッドで使用できるのは、full 文字列操作のみです。  
  
## 参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)