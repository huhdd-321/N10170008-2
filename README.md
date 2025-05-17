HW#5
簡答
15-4
在FileInfo物件建立新文字檔是使用______方法，新增文字內容至檔尾是呼叫______方法來開啟檔案。1.CreateText 2.AppendText
15-5
檔案對話方塊依用途分為2種控制項：______和______。OpenFileDialog 和 SaveFileDialog

實作
10-3
namespace VehicleApp
{
    // 定義介面 IPrice
    public interface IPrice
    {
        double GetPrice();
    }

    // Car 類別實作 IPrice 介面
    public class Car : IPrice
    {
        // 公開屬性
        public double Price { get; set; }
        public string Name { get; set; }

        // 建構子
        public Car(string name, double price)
        {
            Name = name;
            Price = price;
        }

        // 實作 GetPrice 方法
        public double GetPrice()
        {
            return Price;
        }

        // 額外的方法：取得車名
        public string GetName()
        {
            return Name;
        }
    }

    // 主程式
    class Program
    {
        static void Main(string[] args)
        {
            Car myCar = new Car("Toyota", 850000);
            Console.WriteLine("車名: " + myCar.GetName());
            Console.WriteLine("價格: " + myCar.GetPrice() + " 元");
        }
    }
}


11-1
namespace MethodOverloadingDemo
{
    public class MathUtility
    {
        // 過載方法：計算 int 的平方
        public int Cube(int number)
        {
            return number * number;
        }

        // 過載方法：計算 double 的平方
        public double Cube(double number)
        {
            return number * number;
        }

        // 過載方法：找出三個整數中的最小值
        public int MinElement(int a, int b, int c)
        {
            return Math.Min(a, Math.Min(b, c));
        }

        // 過載方法：找出四個整數中的最小值
        public int MinElement(int a, int b, int c, int d)
        {
            return Math.Min(a, Math.Min(b, Math.Min(c, d)));
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            MathUtility util = new MathUtility();

            // 測試 Cube 方法
            Console.WriteLine("Cube of 3 (int): " + util.Cube(3));           // 輸出 9
            Console.WriteLine("Cube of 2.5 (double): " + util.Cube(2.5));   // 輸出 6.25

            // 測試 MinElement 方法
            Console.WriteLine("Min of (3, 7, 2): " + util.MinElement(3, 7, 2));               // 輸出 2
            Console.WriteLine("Min of (5, 9, 1, 4): " + util.MinElement(5, 9, 1, 4));         // 輸出 1
        }
    }
}


12-3
namespace UnitConversionApp
{
    // 定義委派型別
    delegate double ConvertToInches(double value);

    public class UnitConverter
    {
        // 英尺轉英吋
        public double FeetToInches(double feet)
        {
            return feet * 12;
        }

        // 英碼轉英吋
        public double YardsToInches(double yards)
        {
            return yards * 3 * 12;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            UnitConverter converter = new UnitConverter();
            ConvertToInches convertDelegate;

            Console.WriteLine("請選擇要轉換的單位：");
            Console.WriteLine("1. 英尺 (Feet) → 英吋");
            Console.WriteLine("2. 英碼 (Yards) → 英吋");
            Console.Write("請輸入選項 (1 或 2)：");
            string option = Console.ReadLine();

            if (option == "1")
            {
                convertDelegate = new ConvertToInches(converter.FeetToInches);
            }
            else if (option == "2")
            {
                convertDelegate = new ConvertToInches(converter.YardsToInches);
            }
            else
            {
                Console.WriteLine("無效的選項！");
                return;
            }

            Console.Write("請輸入數值：");
            if (double.TryParse(Console.ReadLine(), out double input))
            {
                double inches = convertDelegate(input);
                Console.WriteLine($"轉換結果：{inches} 英吋

13-3
public partial class Form1 : Form
{
    private Label trafficLightLabel;

    public Form1()
    {
        InitializeComponent();

        // 建立 Label 控制項
        trafficLightLabel = new Label();
        trafficLightLabel.Text = "紅燈";
        trafficLightLabel.TextAlign = ContentAlignment.MiddleCenter;
        trafficLightLabel.Font = new Font("Arial", 24, FontStyle.Bold);
        trafficLightLabel.Size = new Size(200, 200);
        trafficLightLabel.BackColor = Color.Red; // 預設紅燈
        trafficLightLabel.Location = new Point(50, 50);

        // 加入 MouseDown 事件監聽器
        trafficLightLabel.MouseDown += TrafficLightLabel_MouseDown;

        // 把 Label 加到 Form 上
        this.Controls.Add(trafficLightLabel);
    }

    private void TrafficLightLabel_MouseDown(object sender, MouseEventArgs e)
    {
        if (e.Button == MouseButtons.Left)
        {
            trafficLightLabel.BackColor = Color.Yellow;
            trafficLightLabel.Text = "黃燈";
        }
        else if (e.Button == MouseButtons.Right)
        {
            trafficLightLabel.BackColor = Color.Green;
            trafficLightLabel.Text = "綠燈";
        }
    }
}


