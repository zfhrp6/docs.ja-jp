---
title: ".NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ファイル アクセス, Visual Basic のファイル I/O"
  - "ファイルの属性, 判断"
  - "ストリーム, 基本的な操作"
  - "ファイルのアクセス許可"
  - "ストリーム"
  - "ストリーム, 定義"
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# .NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.IO> 名前空間のクラスは、ドライブ、ファイル、ディレクトリの操作に使用されます。  
  
 <xref:System.IO> 名前空間には <xref:System.IO.File> クラスと <xref:System.IO.Directory> クラスが含まれています。これらのクラスを使用すると、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] でファイルとディレクトリを操作できます。 これらのオブジェクトのメソッドは静的メンバーまたは共有メンバーなので、あらかじめクラスのインスタンスを作成しなくてもメンバーを直接使用できます。 これらのクラスに関連するクラスとして、<xref:System.IO.FileInfo> クラスと <xref:System.IO.DirectoryInfo> クラスがあります。`My` 機能を使用しているユーザーには使い慣れたクラスです。 これらのクラスを使用するには、名前を完全修飾するか、または、関係するコードの先頭に `Imports` ステートメントを記述して、適切な名前空間をインポートする必要があります。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
> [!NOTE]
>  このセクションのそのほかのトピックでは `My.Computer.FileSystem` のクラスではなく、 `System.IO` オブジェクトを使用して、ドライブ、ファイル、およびディレクトリを操作します。 `My.Computer.FileSystem` オブジェクトは [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のプログラムで使用する主な目的としています。 `System.IO` のクラスは [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] をサポートする [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] などの言語で使用するためのものです。  
  
## <a name="definition-of-a-stream"></a>ストリームの定義  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] では、ファイルに対する読み取りと書き込みをサポートするストリームを使用できます。 ストリームとは、1 次元の連続したデータの集まりと考えることができます。ストリームには先頭と末尾があり、カーソルでストリーム内での現在の位置を示します。  
  
 ![Filestream 内の現在の位置を示すカーソル](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>ストリームの操作  
 ストリームに格納されているデータは、メモリ、ファイル、または TCP/IP ソケットから取得したものです。 ストリームに対しては、次の基本操作を実行できます。  
  
-   読み取り。 ストリームを読み取ったり、文字列やバイト配列などのデータ構造にストリームからデータを転送したりできます。  
  
-   **書き込み**。 ストリームに書き込んだり、データ ソースからストリームにデータを転送したりできます。  
  
-   **シーク**。 ストリーム内の現在の位置をクエリおよび変更できます。  
  
 詳細については、「 [Composing Streams](../Topic/Composing%20Streams.md)」を参照してください。  
  
## <a name="types-of-streams"></a>ストリームの種類  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] では、ストリームは <xref:System.IO.Stream> クラスで表されます。これは、その他のすべてのストリームのための抽象クラスです。 <xref:System.IO.Stream> クラスのインスタンスを直接作成することはできません。これを実装するいずれかのクラスを使用する必要があります。  
  
 ストリームにはさまざまな種類がありますが、ファイルの入出力 (I/O) を処理するという目的のために最も重要なのは、ファイルに対する読み取りと書き込みを実現する <xref:System.IO.FileStream> クラスと、分離ストレージに対するファイルやディレクトリの作成を実現する <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> クラスです。 この他、ファイル I/O を処理する場合、以下のようなストリームを使用できます。  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>  
  
 次の表は、ストリームで一般的に実行するタスクの一覧です。  
  
|||  
|-|-|  
|目的|参照トピック|  
|データ ファイルに対する読み取りと書き込み|[方法: 新しく作成されたデータ ファイルに対して読み書きする](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)|  
|ファイルのテキストの読み取り|[方法: ファイルからテキストを読み取る](../Topic/How%20to:%20Read%20Text%20from%20a%20File.md)|  
|テキストのファイルへの書き込み|[方法: ファイルにテキストを書き込む](../Topic/How%20to:%20Write%20Text%20to%20a%20File.md)|  
|文字列からの文字の読み取り|[方法: 文字列から文字を読み取る](../Topic/How%20to:%20Read%20Characters%20from%20a%20String.md)|  
|文字列への文字の書き込み|[方法: 文字列に文字を書き込む](../Topic/How%20to:%20Write%20Characters%20to%20a%20String.md)|  
|データの暗号化|[データの暗号化](../Topic/Encrypting%20Data.md)|  
|データの復号化|[データの復号化](../Topic/Decrypting%20Data.md)|  
  
## <a name="file-access-and-attributes"></a>ファイル アクセスと属性  
 ファイルの作成、オープン、および共有の方法は、<xref:System.IO.FileAccess>、<xref:System.IO.FileMode>、<xref:System.IO.FileShare> の各列挙体で制御できます。これらの列挙体には、<xref:System.IO.FileStream> クラスのコンストラクターで使用するフラグが含まれています。 たとえば、<xref:System.IO.FileStream> を開くかまたは新規作成するときに、ファイルを追加書き込み用に開くかどうか、指定のファイルが存在しない場合にファイルを新規作成するかどうか、ファイルを上書きするかどうかなどを、<xref:System.IO.FileMode> 列挙体で指定できます。  
  
 <xref:System.IO.FileAttributes> 列挙体を使用すると、ファイル固有の情報を収集できます。 <xref:System.IO.FileAttributes> 列挙体は、格納されているファイルの属性を返します。これらの属性によって、圧縮ファイル、暗号化されたファイル、隠しファイル、読み取り専用ファイル、アーカイブ、ディレクトリ、システム ファイル、一時ファイルであるかどうかがわかります。  
  
 次の表は、ファイル アクセスとファイル属性に関連するタスクの一覧です。  
  
|||  
|-|-|  
|**目的**|**参照トピック**|  
|ログ ファイルのオープンとテキストの追加|[方法: ログ ファイルを開いて情報を追加する](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)|  
|ファイルの属性の判断|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>ファイルのアクセス許可  
 ファイルおよびディレクトリに対するアクセスの制御は、<xref:System.Security.Permissions.FileIOPermission> クラスで行うことができます。 これは、Web フォームの開発者には特に重要な場合があります。既定では、Web フォームは、ASPNET という名前の特別なローカル ユーザー アカウントのコンテキストで実行されます。ASPNET は、 [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] および [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] のインストール時に作成されます。 ASPNET ユーザー アカウントはアクセス許可が制限されているため、アプリケーションがリソースへのアクセスを要求したときに、ユーザーが処理を実行できない場合があります (たとえば、Web アプリケーションからファイルへの書き込みなど)。 詳細については、「[Security Permissions](http://msdn.microsoft.com/ja-jp/b03757b4-e926-4196-b738-3733ced2bda0)」(セキュリティのアクセス許可) と <xref:System.Security.Permissions.FileIOPermission> に関するページを参照してください。  
  
## <a name="isolated-file-storage"></a>分離ファイル ストレージ  
 分離ストレージとは、ファイルを扱うときに、必要なアクセス許可をユーザーまたはコードが持っていないために生じる問題を解決するためのものです。 分離ストレージでは、各ユーザーにデータ コンパートメントが割り当てられます。このデータ コンパートメントには、1 つまたは複数のストアを保持できます。 ストア間は、ユーザーおよびアセンブリごとに分離できます。 ストアにアクセスできるのは、それを作成したユーザーおよびアセンブリのみです。 ストアは、完全な仮想ファイル システムとして機能します。つまり、ストア内でディレクトリやファイルを作成および操作できます。  
  
 次の表は、分離ファイル ストレージに一般に関連するタスクの一覧です。  
  
|||  
|-|-|  
|目的|参照トピック|  
|分離ストアの作成|[方法: 分離ストレージでストアを取得する](../Topic/How%20to:%20Obtain%20Stores%20for%20Isolated%20Storage.md)|  
|分離ストアの列挙|[方法: 分離ストレージでストアを列挙する](../Topic/How%20to:%20Enumerate%20Stores%20for%20Isolated%20Storage.md)|  
|分離ストアの削除|[方法: 分離ストレージでストアを削除する](../Topic/How%20to:%20Delete%20Stores%20in%20Isolated%20Storage.md)|  
|分離ストレージのファイルまたはディレクトリの作成|[方法: 分離ストレージでファイルおよびディレクトリを作成する](../Topic/How%20to:%20Create%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|分離ストレージのファイルの検索|[方法: 分離ストレージ内でファイルおよびディレクトリを検索する](../Topic/How%20to:%20Find%20Existing%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|分離ストレージのファイルに対する読み取りと書き込み|[方法: 分離ストレージ内でファイルの読み取りと書き込みを行う](../Topic/How%20to:%20Read%20and%20Write%20to%20Files%20in%20Isolated%20Storage.md)|  
|分離ストレージのファイルまたはディレクトリの削除|[方法: 分離ストレージでファイルおよびディレクトリを削除する](../Topic/How%20to:%20Delete%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
  
## <a name="file-events"></a>ファイルのイベント  
 <xref:System.IO.FileSystemWatcher> コンポーネントを使用すると、自システム上のファイルとディレクトリ、またはネットワークでアクセスできる任意のコンピューター上のファイルとディレクトリの変更を監視できます。 たとえば、ファイルが変更されたときに、その旨をユーザーに警告することが必要な場合があります。 変更が行われると、1 つまたは複数のイベントが発生し、バッファーに格納され、<xref:System.IO.FileSystemWatcher> コンポーネントに渡されて処理されます。  
  
## <a name="see-also"></a>関連項目  
 [ストリームの構成](../Topic/Composing%20Streams.md)   
 [ファイルおよびストリーム入出力](../Topic/File%20and%20Stream%20I-O.md)   
 [非同期ファイル I/O](../Topic/Asynchronous%20File%20I-O.md)   
 [.NET Framework のファイル I/O とファイル システムで使用するクラス (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)