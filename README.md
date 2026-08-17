import java.util.Scanner;
public class FitnessTracker {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);

        System.out.println("\n\n*=========================================*");
        System.out.println("                FITNESS TRACKER            ");
        System.out.println("*=========================================*\n\n");

        System.out.println("Enter Number of days in this month: ");
        int days = sc.nextInt();

        int steps[] = new int[days];

        int totalsteps = 0;
        int totalcaloriesburned = 0;
        int totalDistance = 0;
        int totalcaloriesConsumed = 0;

        int currentStreak = 0;
        int longestStreak = 0;

        for(int i = 0; i < days; i++)
        {
            System.out.println("\n\n=================================");
            System.out.println("DAY " +(i+1));
            System.out.println("=================================\n\n");

            System.out.println("Enter Today's Steps: ");
            
            steps[i] = sc.nextInt();
            totalsteps += steps[i];

            double caloriesburned = steps[i] * 0.04;

            double distance = steps[i] * 0.0008;

            totalcaloriesburned += caloriesburned;
            totalDistance += distance;

            if (steps[i] >= 10000)
            {
                currentStreak++;

                if(currentStreak > longestStreak)
                    longestStreak = currentStreak;
                
            } else {
                currentStreak = 0;
            }

            //Junk Food
            System.out.println("\nSelect Junk Food: ");

            System.out.println("1. Burger (300 kcal)");
            System.out.println("2. Pizza (285 kcal)");
            System.out.println("3. Pani Puri (210 kcal)");
            System.out.println("4. Momos (350 kcal)");
            System.out.println("5. Soft Drink (140 kcal)");
            System.out.println("6. Ice Cream (210 kcal)");
            System.out.println("7. Spring Roll (180 kcal)");
            System.out.println("8. Samosa (220 kcal)");
            System.out.println("9. Bread Pakoda (250 kcal)");
            System.out.println("10. None");

            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            int caloriesPerItem = 0;
            String food = "None";

            switch(choice)
            {
                case 1:
                    food = "Burger";
                    caloriesPerItem = 300;
                    break;
                    
                case 2:
                    food = "Pizza";
                    caloriesPerItem = 285;
                    break;

                case 3:
                    food = "Pani Puri";
                    caloriesPerItem = 210;
                    break;

                case 4:
                    food = "Momos";
                    caloriesPerItem = 350;
                    break;

                case 5:
                    food = "Soft Drink";
                    caloriesPerItem = 140;
                    break;

                case 6:
                    food = "Ice Cream";
                    caloriesPerItem = 210;
                    break;

                case 7:
                    food = "Spring Roll";
                    caloriesPerItem = 180;
                    break;

                case 8:
                    food = "Samosa";
                    caloriesPerItem = 220;
                    break;

                case 9:
                    food = "Bread Pakoda";
                    caloriesPerItem = 250;
                    break;

                case 10:
                    food = "None";
                    caloriesPerItem = 0;
                    break;

                default:
                    System.out.println("Invalid Choice!");

            }

            int quantity = 0;
            if(choice != 10)
            {
                System.out.println("Enter Quantity: ");
                quantity = sc.nextInt();
            }

            int caloriesConsumed = caloriesPerItem * quantity;
            totalcaloriesConsumed += caloriesConsumed;
            double netCalories = caloriesburned - caloriesConsumed;
            
            
            //Daily Report
            System.out.println("\n\n___________________________________________________________________\n\n\n");
            System.out.println("===================================================================");
            System.out.println("                          DAILY REPORT                             ");
            System.out.println("===================================================================\n\n\n");
            System.out.println("\n\n🔸 Steps Walked: " +steps[i]);
            System.out.println("🔸 Distance Walked: " +distance+ " km\n");
            System.out.println("🔸 Calories Burned: " +caloriesburned+ " Kcal\n");
            System.out.println("🔸 Junk Food: " +food);
            System.out.println("🔸 Calories Consumed: " +caloriesConsumed+ " Kcal\n");
            System.out.println("🔸 Net Calories: " +netCalories+ " Kcal\n");

            if(steps[i] >= 10000)
            {
                System.out.println("Outstanding! You crushed every goal today. 🏆");
            } else {
                System.out.println("Missing one day doesn't erase your progress. Start again today.😎");
            }

            if(steps[i] >= 10000 && netCalories > 0)
            {
                System.out.println("Excellent! Keep pushing. You're getting stronger.😋😎");
            } else if(steps[i] >= 10000)
            {
                System.out.println("Great Walking! Don't quit. Keep going.😃");
            } else {
                System.out.println("Keep moving! Be better than yesterday.🤓");
            }

            //Monthly Report
            double averageSteps = totalsteps / days;
            double averageDistance = totalDistance / days;
            double caloriesBurned = totalcaloriesburned / days;

            System.out.println("\n\n__________________________________________________________________________\n\n\n");
            System.out.println("==========================================================================");
            System.out.println("                          MONTHLY REPORT                                  ");
            System.out.println("==========================================================================\n\n\n");
            System.out.println("🔹 Total Days: " +days+"\n");
            System.out.println("🔹 Total Steps: " +totalsteps+"\n");
            System.out.println("🔹 Average Day Steps: " +averageSteps+"\n");
            System.out.println("🔹 Total Distance Walked: " +totalDistance+ " km\n");
            System.out.println("🔹 Average Distance: " +averageDistance+ " km/day\n");
            System.out.println("🔹 Total Calories Consumed: " +totalcaloriesConsumed+ " Kcal\n");
            System.out.println("🔹 Total Junk Food Calories: " +totalcaloriesConsumed+ " Kcal\n");
            System.out.println("🔹 Net Calories: " +(totalcaloriesburned - totalcaloriesConsumed)+ " Kcal\n");

            System.out.println("Longest Step Goal Streak " +longestStreak+ " days.\n");

            //Rating

            if(longestStreak >= 25)
            {
                System.out.println("PROUD OF YOU!🥳");
                System.out.println("Discipline creates results.");
            } else if(longestStreak >= 15)
            {
                System.out.println("YOU'RE ON FIRE!🔥");
                System.out.println("15 days down. This is just the beginning!");
            } else if(longestStreak >= 7)
            {
                System.out.println("GREAT JOB!🎉🎉");
                System.out.println("Consistency beats perfection.");

            } else if(longestStreak < 7)
            {
                System.out.println("STAY STRONG!💪");
                System.out.println("You can do better, Never miss twice.");
            }

            
            System.out.println("\n\n----- THANK YOU FOR USING MY FITNESS TRACKER -----\n\n\n");
            
        }
    }
}
