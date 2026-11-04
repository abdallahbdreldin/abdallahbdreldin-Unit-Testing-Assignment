# Naming Convention (R1)

These rules apply to both assignment parts, DriveNow and ParkSmart.

## Test project names

Start each test project name with its part, then add the test type:

- DriveNow: `DriveNow.LegacyTests`, `DriveNow.UnitTests`, `DriveNow.ArchitectureTests`
- ParkSmart: `ParkSmart.UnitTests`, `ParkSmart.ArchitectureTests`

Use the same name for the project folder and `.csproj` file.

## Test class and file names

Name each test class `<ClassUnderTest>Tests`. Put one test class in a file with the same name and a `.cs` extension.

Examples:

- `ReceiptServiceTests` is stored in `ReceiptServiceTests.cs`.
- `RentalMathTests` is stored in `RentalMathTests.cs`.
- `ParkingSessionTests` is stored in `ParkingSessionTests.cs`.

## R2 — Test Method Naming Convention

### Comparing Naming Styles

I considered three common test naming conventions:

1. **Method_Scenario_ExpectedResult**
   - Clearly identifies the method being tested, the scenario, and the expected result.
   - Example: `UpgradeTier_ExactlyFiveRentals_Silver`

2. **Should_X_When_Y**
   - Describes the expected behavior and the condition under which it should happen.
   - Example: `Should_SetSilverTier_WhenCustomerHasExactlyFiveRentals`

3. **Given_When_Then**
   - Describes the test using three parts: the initial condition, the action, and the expected outcome.
   - Example: `GivenFiveCompletedRentals_WhenUpgradingTier_ThenSilverTierIsAssigned`

### Chosen Convention

I choose **Method_Scenario_ExpectedResult**
	because I find it more readable and cleaner.
	It allows developers to understand what the test is testing and what result is expected just by reading its name,
	without needing to open the test implementation.

### Examples from DriveNow

Using `LoyaltyService.UpgradeTier()`:

- `UpgradeTier_NoRentals_None`
- `UpgradeTier_ExactlyFiveRentals_Silver`
- `UpgradeTier_ExactlyThirtyRentals_Platinum`

All test methods across the project will follow this naming convention.

### R3 — Test Doubles and Test Data Naming

- Hand-written Fake classes must start with `Fake`, followed by the dependency name (e.g. `FakeBookingRepository`).
- Hand-written Spy classes must start with `Spy`, followed by the dependency name (e.g. `SpySmsSender`).
- Hand-written Stub classes must start with `Stub`, followed by the dependency name (e.g. `StubPaymentGateway`).
- Hand-written Dummy classes must start with `Dummy`, followed by the dependency name (e.g. `DummyLogger`).
- Bogus Faker classes must end with `Faker` (e.g. `CustomerFaker`, `VehicleFaker`).
- AutoFixture customization classes must end with `Customization` (e.g. `CustomerCustomization`).
- Custom AutoFixture xUnit attributes must end with `AutoDataAttribute` (e.g. `DriveNowAutoDataAttribute`).

## Production code names and namespaces (R4)

- **Interfaces:** Start interface names with `I` , for example `IReceiptFormatter`. ParkSmart currently has no production interfaces.
- **Repositories:** Put DriveNow repositories in `DriveNow.Infrastructure.Repositories`. End repository names with `Repository`; ParkSmart currently has no repositories.
- **Services:** Put domain services in `DriveNow.Domain.Services`  . ParkSmart currently has no services.

