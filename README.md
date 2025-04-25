# import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Input } from "@/components/ui/input"; import { Button } from "@/components/ui/button"; import { CheckCircle, XCircle } from "lucide-react";

const addressData = { "0x816...a813": 10, "0xfD4...fEDD": 10, "0x216...d5fe": 10, "0x452...3Bc9": 10, "0xC2F...1e51": 10, "0x8DD...6C4d": 10, "0x0De...6e9F": 10, "0x46f...581B": 10, "0xf56...5b62": 10, "0x4Bb...a1eE": 10, "0xA80...d316": 10, "0xFDF...d42E": 10, "0x9FF...ec2C": 10, "0x916...f329": 10, "0xC76...3f86": 10, "0x949...5f0C": 10, "0x8c0...E4EA": 10, "0xCd8...Ef88": 10, "0x995...AB70": 10, "0xE65...bd35": 10, "0xfb2...476a": 10, "0x188...16EA": 10, "0x6Ac...6a3C": 10, "0xfBc...B5df": 10, "0xE22...7f37": 10, "0x77e...7899": 10, "0x991...9Cce": 10, "0xf89...d784": 10, "0xB20...44C2": 10, "0xA15...96Cd": 10, "0x25E...A287": 10, "0x19C...4339": 10, "0xE52...8D7e": 10, "0x499...5980": 10, "0x031...AFB3": 10, "0xAd2...1611": 10 };

export default function UXUYChecker() { const [input, setInput] = useState(""); const [bonus, setBonus] = useState<number | null>(null);

const handleCheck = () => { const address = Object.keys(addressData).find(addr => input.startsWith(addr.slice(0, 5)) && input.endsWith(addr.slice(-4))); if (address) { setBonus(addressData[address]); } else { setBonus(0); } };

return ( <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-gray-900 to-black p-4"> <Card className="max-w-md w-full shadow-2xl bg-white/5 backdrop-blur border-white/10 border"> <CardContent className="p-6"> <h1 className="text-xl font-bold text-white mb-4 text-center">UXUY Checker by Rasel Ahmed</h1> <Input placeholder="Paste wallet address" value={input} onChange={e => setInput(e.target.value)} className="mb-4 bg-white/10 text-white placeholder-white" /> <Button onClick={handleCheck} className="w-full mb-4">Check Bonus</Button>

{bonus !== null && (
        <div className="flex items-center justify-center gap-2">
          {bonus > 0 ? (
            <>
              <CheckCircle className="text-green-400" />
              <span className="text-white">Congrats! You earned {bonus} UXUY</span>
            </>
          ) : (
            <>
              <XCircle className="text-red-400" />
              <span className="text-white">Sorry! No bonus found for this address.</span>
            </>
          )}
        </div>
      )}
    </CardContent>
  </Card>
</div>

); }
