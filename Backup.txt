// Import Utilities
import java.util.Map;
import java.util.Scanner;

class Main {

    public void main() {}

    static public class Backpack {
        // Private variables
        private int itemsStored;
        private int capacity = 8;
        private String[] items = new String[capacity];

        // Encapsulation for Object Backpack
        public Backpack() {}

        // Get Item Count
        public int getItemCount() {
            return itemsStored;
        }

        // Get Maximum Capacity
        public int getCapacity() {
            return capacity;
        }

        // Get Item's Name
        public String getItemName(int number) {
            return items[number];
        }

        // Set Amount of Items Stored in Backpack
        public void setItemsStored(int newItemsStored) {
            this.itemsStored = newItemsStored;
        }

        // Remove an object
        public void removeItem(int slot) {
            items[slot] = null;
        }

        // Set Item's Name in Backpack
        public void setItemName(int number, String name) {
            items[number] = name;
        }
    }

    public static void main(String[] args) {
        // Declare Backpack Object
        Backpack backpack = new Backpack();
        Scanner scanner = new Scanner(System.in);
        do {

            // Declare Keyboard Scanner
            String command = scanner.next();

            // Possible Commands
            if (command.equals("/getBackpackCapacity")) {
                System.out.println("Your backpack has a capacity of " + backpack.getCapacity() + " items.");
            } 
            
            else if (command.equals("/getBackpackItemCount")) {
                System.out.println("You have " + backpack.getItemCount() + " items stored in your backpack.");
            } 
            
            else if (command.equals("/addItem")) {
                if (backpack.getCapacity() >= backpack.getItemCount() + 1) {

                    // Add to Item Count
                    backpack.setItemsStored(backpack.getItemCount() + 1);

                    // Declare Keyboard Scanners
                    System.out.println("Name of the item:");
                    String itemNamed = scanner.next();

                    // Set Name
                    backpack.setItemName(backpack.getItemCount()-1, itemNamed);

                    System.out.println("You have added the item " +backpack.getItemName(backpack.getItemCount()-1)+ " to your backpack.");
                } 
                
                else {
                    System.out.println("Your backpack is at maximum capacity. Remove an item to add another one in your backpack.");
                }
            }

            else if (command.equals("/removeItem")) {

                System.out.println("Slot number in the backpack:");
                String itemNumbers = scanner.next();

                // Transform String to Integer
                int itemNumbered = Integer.parseInt(itemNumbers);

                if (backpack.getItemName(itemNumbered) == null) {
                    System.out.println("Illegal Command. Cannot delete inexistant item. Try again.");
                    continue;
                }
                else {
                    System.out.println("You have removed the item " +backpack.getItemName(itemNumbered)+ ".");
                    backpack.removeItem(itemNumbered);
                }

            }
            
            else if (command.equals("/changeItemName")) {
                // Declare Keyboard Scanners
                System.out.println("Name of the item:");
                String named = scanner.next();

                System.out.println("Slot number in the backpack:");
                String numbers = scanner.next();

                // Transform String to Integer
                int numbered = Integer.parseInt(numbers);

                // Check Existence of that item
                if (backpack.getItemCount() < numbered) {
                    System.out.println("Illegal command. There is no item in this slot. Try again.");
                    continue;
                }
                else if (backpack.getItemCount() == 0 & numbered == 0) {
                    System.out.println("Illegal command. There is no item in this slot. Try again.");
                    continue;
                }
                // Set Name
                backpack.setItemName(numbered, named);
                System.out.println("You have named the item number " + numbered + " " + named + ".");
            } 

            else if (command.equals("/listItems")) {
                System.out.println("You have in your backpack:");
                for (int i = 0; i < backpack.getCapacity(); i++) {
                    if (backpack.getItemName(i) == null) {
                        System.out.println("Nothing");
                    }
                    else {
                        System.out.println(backpack.getItemName(i));
                    }
                }
            }
            
            else if (command.equals("/help")) {
                System.out.println("/getBackpackCapacity");
                System.out.println("/getBackpackItemCount");
                System.out.println("/addItem");
                System.out.println("/removeItem");
                System.out.println("/changeItemName");
                System.out.println("/listItems");
                System.out.println("/exit");
            } 

            else if (command.equals("/exit")) {
                // Declaring Keyboard Scanner
                System.out.println("Are you sure? Y/N");
                String choices = scanner.next();

                // Choices
                if (choices.equals("Y") || choices.equals("y")) {
                    break;
                }
                else if (choices.equals("N") || choices.equals("n")) {
                }
                else {
                    System.out.println("Illegal command. Respond using Y or N.");
                }

            } 
            
            else {
                System.out.println("Illegal command. Try again");
            }

        } while (true);
        // Close Keyboard Scanner Object
        scanner.close();
    }

}