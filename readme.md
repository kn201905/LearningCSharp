# 前置き

　C# はオブジェクト指向プログラミング（＝OOP）と相性がよく、簡単で理解もしやすいため、まずは動くものを作ってみて感覚を是非つかんでみてください。

　以下に示した流れでコードを書いていくと、文法が分からない状態でコードができあがっていくから少々気持ち悪く感じると思いますが、文法はコードを開発しながら理解してみてください。最近、非同期機構（コルーチン）やクロージャが分からない、と言っている人を多く見かけますが、そういうものは文法書を読んでも理解は難しいでしょう。一部の人は文法書を読んだだけで理解できると思いますが、そういう人は少数派だと思います。とにかく動かしてみて、その動きから理解するのが間違いなく簡単だと思います。

# C# のインストール

　インターネットで C#、インストール、と検索してください。Visual Studio をインストールするときに、「.NET デスクトップ開発」にチェックマークを付けてインストールするだけでＯＫ。Visual Studio は、後で必要なものが出てきたら、いつでも自由に追加インストールすることができるため、気楽にどうぞ。

　とりあえず、Microsoft の公式ページから、Community 版をダウンロードしてください。Community 版以外は有料となります。

![01](https://github.com/kn201905/LearningCSharp/assets/50472422/f0d8b9fa-034a-425f-b7f5-b3eb19a435d4)

　インストーラを起動したら、「.NET デスクトップ開発」にチェックマークを付けてインストールしてください。（私は他にも開発しているものがありますので、「.NET デスクトップ開発」以外にもチェックマークが付いていますが、気にしないでください。）
 
![02](https://github.com/kn201905/LearningCSharp/assets/50472422/45a63664-43cc-49e4-b510-59f8978302ae)

# まずは動くものを作る

　ファイル -> 新規作成 -> プロジェクト で、C# の「Windows フォームアプリ」を作成。

　このプロジェクトは試しに作るだけなので、名前などは適当でＯＫ。分からなければ、ＯＫボタンをどんどん押していってもらえばよい（１、２時間後には消すプロジェクトになるだろうし、、）。
 
![01_01](https://github.com/kn201905/LearningCSharp/assets/50472422/f7e2154e-dca5-4599-98f9-2c5caf18176f)


# とりあえず実行

　プロジェクトが開いたら、とりあえず「F5」キーで実行。（メニューを利用する場合は、デバッグ -> デバッグの開始）

　ウィンドウが１枚開けばＯＫ。「✕」ボタンでウィンドウを閉じて終了。

# 動作したファイルの確認

　できあがるファイルで重要なのは下の３つだけ。namespace のところに表示されるものは、プロジェクトを作成する時に付けた名前になっていると思う。

(ア) Program.cs（ソリューションエクスプローラで、Program.cs をダブルクリック）
```cs
namespace TestProgram
{
	static class Program
	{
		[STAThread]
		static void Main()
		{
			Application.EnableVisualStyles();
			Application.SetCompatibleTextRenderingDefault(false);
			Application.Run(new Form1());
		}
	}
}
```

(イ) Form1.cs（ソリューションエクスプローラで Form1.cs を右クリックして、「コードの表示」をクリック）
```cs
namespace TestProgram
{
	public partial class Form1 : Form
	{
		public Form1()
		{
			InitializeComponent();
		}
	}
}
```

(ウ) Form1.Designers.cs（ソリューションエクスプローラで、Forms1.cs の左側の ▶ マークをクリックすると、Form1.Designers.cs が表示されるので、それをダブルクリック）
```cs
namespace TestProgram
{
	partial class Form1
	{
		private System.ComponentModel.IContainer components = null;

		protected override void Dispose(bool disposing)
		{
			if (disposing && (components != null))
			{
				components.Dispose();
			}
			base.Dispose(disposing);
		}

		#region Windows フォーム デザイナーで生成されたコード

		private void InitializeComponent()
		{
			this.components = new System.ComponentModel.Container();
			this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
			this.ClientSize = new System.Drawing.Size(800, 450);
			this.Text = "Form1";
		}

		#endregion
	}
}

```

# namespace について

　namespace は、ファイルが分かれてても同じプログラムのコードであることを示すために利用するもの。

