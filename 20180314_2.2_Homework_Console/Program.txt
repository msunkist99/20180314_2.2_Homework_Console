using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _20180314_2._2_Homework_Console
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Title = "_20180314_2.2_Homework_Console";

            Cards cardDeck = new Cards();

            foreach (Card card in cardDeck.DeckOfCards)
            {
                Console.WriteLine(card.CardName);
            }

            Console.ReadLine();

            // I am going to use a STATIC method within the Cards class - without creating an instance of the CardDeck class
            Cards.WriteALineToTheConsole();

            Console.WriteLine(cardDeck.DrawRandomCard());

            Console.ReadLine();
        }
    }



    class Card
    {
        public int Suit { get; set; }
        public int Value { get; set; }
        public String CardName
        {
            get
            {
                return GetValueName(Value) + " of " + GetSuitName(Suit);
            }
        }

        private string GetSuitName(int suit)
        {
            if (suit == 0)
            {
                return "Hearts";
            }
            else if (suit == 1)
            {
                return "Diamonds";
            }
            else if (suit == 2)
            {
                return "Clubs";
            }
            else if (suit == 3)
            {
                return "Spades";
            }
            else
            {
                return "unknown";
            }
        }

        private string GetValueName(int value)
        {
            if (value == 13)
            {
                return "King";
            }
            else if (value == 12)
            {
                return "Queen";
            }
            else if (value == 11)
            {
                return "Jack";
            }
            else if (value == 1)
            {
                return "Ace";
            }
            else if ((value > 1) && (value < 11))
            {
                return value.ToString();
            }
            else
            {
                return "unknown";
            }
        }
    }



        class Cards
        {
        public List<Card> DeckOfCards { get;  }

        // constructor 1 - this code is excuted when a CardDeck object is created from this class
        public Cards()
        {
            DeckOfCards = new List<Card>();
            for (int suit = 0; suit <= 3; suit++)
            {
                for (int value = 1; value <= 13; value++)
                {
                    Card card = new Card() { Suit = suit, Value = value  };

                    this.DeckOfCards.Add(card);
                }
            }
        }
    

        public string DrawRandomCard()
        {
            Random random = new Random();
            int randomCardIndex = random.Next(0, this.DeckOfCards.Count + 1);

            return this.DeckOfCards[randomCardIndex].CardName;
        }

        //  This is a STATIC method within the CardDeck class
        //  Because it is STATIC you do not have to create an istance of the CardDeck class to call this method.
        public static void WriteALineToTheConsole()
        {
            Console.WriteLine("\r\nThis line is written from a STATIC method - your randomly drawn card -  ");
        }
    }
}
