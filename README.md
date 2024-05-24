public static void Main(string[] args)
    {
        // Create a SHA256   
        string prefix = "pay_";
        string randomPart = GenerateRandomString(16);
        string finalCode = prefix + randomPart;
        Console.WriteLine($"Generated Code: {finalCode}");
    }
    
    static string GenerateRandomString(int length)
    {
        const string chars = "abcdefghijklmnopqrstuvwxyz0123456789";
        using (RNGCryptoServiceProvider rng = new RNGCryptoServiceProvider())
        {
            byte[] data = new byte[length];
            rng.GetBytes(data);
            StringBuilder result = new StringBuilder(length);
            foreach (byte byteValue in data)
            {
                result.Append(chars[byteValue % chars.Length]);
            }
            return result.ToString();
        }
    }
